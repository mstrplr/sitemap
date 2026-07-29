# Teléfono y CallRail

## La regla

**No hay un solo número de teléfono.** Miami Auto Tinting usa **CallRail**, que
asigna un número de rastreo distinto por fuente de tráfico. Ese es el mecanismo
que permite saber de dónde vienen las llamadas.

Si el bot da siempre el mismo número, **se pierde la atribución** de todo el
tráfico que pase por el bot. Eso rompe la razón de existir de CallRail.

**El bot da el número que corresponde al canal donde está conversando.**

## Mapa de canal → número

Números de rastreo activos (de la plataforma de CallRail):

| Canal / fuente | Número que da el bot |
|---|---|
| Instagram | **786-917-4888** |
| Google My Business | **786-882-4116** |
| TikTok | **786-758-4366** |
| Google Ads (miamiautotintmobile.com) | pool dinámico — ver abajo |
| southmiamitint.com | pool dinámico — ver abajo |
| WhatsApp | no dar número — ya están conversando |

> **786-285-2690 nunca va en esta tabla.** Es la línea real del negocio (el
> WhatsApp) y el destino de routing de CallRail. Ver la sección de WhatsApp.

### Los pools dinámicos

`Miamiautotintmobile.com` (5 números) y `Southmiamitint.com` (7 números) son
**pools de inserción dinámica (DNI)**: CallRail cambia el número mostrado en el
sitio web según el visitante, para atribuir a nivel de sesión.

**El bot no puede usar un pool.** Un pool funciona con el JavaScript de CallRail
en la página, no en una conversación de chat. Si el bot va en el widget web de
esos sitios, hay dos opciones:

1. **No dar número en el chat web** — el número del pool ya está visible en la
   página, y ahí sí funciona el DNI. El bot empuja al agendamiento por chat.
   *(Recomendado — no interfiere con el DNI.)*
2. Crear un número fijo aparte con fuente "Web Chat" para el bot.

### WhatsApp — 786-285-2690

**El WhatsApp del negocio es 786-285-2690.** Ahí es donde vive la conversación
del bot.

**Pero ese número NO se da como "llámanos".** 786-285-2690 es también el
**destino de routing** de CallRail — es la línea real a la que se reenvían las
llamadas de GMB, Instagram y TikTok. Si el bot lo reparte como número para
llamar, la gente marca directo, se salta el rastreo, y esa llamada nunca queda
atribuida a ninguna fuente.

La distinción, que es sutil pero importante:

| | Número |
|---|---|
| Donde el bot **conversa** | 786-285-2690 (WhatsApp) |
| Lo que el bot **da para llamar** | el número de rastreo del canal (ver tabla arriba) |

En la práctica, si ya estás hablando con alguien por WhatsApp casi nunca hace
falta darle un número — la conversación ya está abierta. Recoge los datos y dile
que Jose le escribe.

### Pendiente: número de rastreo para WhatsApp

No existe una fuente "WhatsApp" en CallRail. Vale la pena crearla (*Create
number*) para poder medir si el bot genera llamadas. Sin eso, lo que produzca el
bot se mezcla con el resto y no vas a saber si se paga solo — que es la métrica
que más importa el primer mes.

## Reglas duras para el bot

1. **Nunca dar un número de destino / routing.** Los números a los que CallRail
   reenvía las llamadas son internos. Si el bot los suelta, el cliente llama
   directo, se salta el rastreo, y esa llamada nunca aparece atribuida. Solo se
   dan números **de rastreo**.
2. **Nunca inventar un número.** Si el canal no está en la tabla de arriba y no
   hay número asignado, no improvises — pasa el contacto a Jose y que él llame.
3. **Un número por canal, siempre el mismo.** No rotar ni mezclar.
4. Si el cliente ya está escribiendo por WhatsApp, normalmente **no necesita un
   número** — la conversación ya está abierta. Dar un número ahí es fricción
   innecesaria. Mejor: recoger los datos y decir que Jose le escribe.

## Nota de atribución

Hay dos destinos de routing en la cuenta — 786-285-2690 (el WhatsApp, recibe
GMB / Instagram / TikTok) y 786-269-8850 (recibe los pools de los dos sitios
web). Además hay 43 números desactivados.

- `[CONFIRM]` ¿Los números de rastreo tienen SMS habilitado? Si el bot o Jose van
  a mandar texto de seguimiento, el número tiene que soportar mensajes, no solo
  llamadas.
- `[CONFIRM]` ¿Hay que crear también un *message flow* por defecto? En el
  screenshot aparece "No default message flow is set".

## Dato aparte, relevante

**Instagram ya tiene su propio número de rastreo y su propia fuente.** O sea que
Instagram ya te está generando llamadas medibles.

Eso hace más notable el hueco que encontramos antes: **Forja no tiene conector de
Instagram** (ver `../FORJA-SETUP.md`). Estás invirtiendo en ese canal y midiendo
su retorno, pero el bot no va a poder contestar DMs ahí sin desarrollo aparte.
Vale la pena preguntarle a Horizontes IA si está en el roadmap antes de decidir
cuánto construir alrededor.
