# 🤖 ARI Flow — Clasificación y Respuesta Automatizada de Correos

Flujo desarrollado en **Make.com** que integra **Google Gemini AI**, **Gmail**, **Google Drive** y **Google Sheets** para clasificar correos entrantes, responder consultas frecuentes con base en documentación interna y registrar métricas de seguimiento[cite: 1].

![Diagrama ARI Flow](./ari-flow.png)

## ⚙️ Funcionamiento

1. **Detección y Análisis:** **Gmail** revisa la bandeja de entrada cada 15 minutos y **Google Gemini AI** clasifica la intención del mensaje (identificando si se trata de una *duda Oracle*)
2. **Enrutamiento Condicional (`Router`)
   * **Consulta válida:** Obtiene el documento de referencia desde **Google Drive**, redacta una respuesta contextualizada con **Gemini AI**, envía el correo, lo archiva en una carpeta específica y almacena las variables de estado
   * **Otras consultas (Fallback):** Registra que el correo no requiere respuesta automática
3. **Trazabilidad:** Recupera las variables generadas y añade una fila en **Google Sheets** con el historial de cada interacción[cite: 1].

## 🛠️ Herramientas Utilizadas

* **Orquestación:** Make.com (`Router`, `Set/Get variables`)
* **Inteligencia Artificial:** Google Gemini AI
* **Ecosistema Google:** Gmail, Google Drive, Google Sheets
