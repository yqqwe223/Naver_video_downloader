# Naver Media Analyzer (Analizador de Contenido Multimedia de Naver)

> 🔍 Herramienta frontend ligera con fines educativos y de investigación, que permite extraer metadatos de contenido público en Naver

🌐 Demostración en línea: [https://twittervideodownloaderx.com/naver_downloader_sp](https://twittervideodownloaderx.com/naver_downloader_sp)

---

## 📋 Descripción del Proyecto

Este proyecto ha sido desarrollado con fines educativos y de investigación técnica. Se trata de una utilidad frontend ligera diseñada para ayudar a desarrolladores y estudiantes a comprender cómo extraer metadatos estructurados de páginas públicas de Naver (Naver Blog, Naver TV, Naver Post, etc.), utilizando interfaces de vista previa web estándar y APIs de datos estructurados.

> 🎯 Casos de uso recomendados:
> - Organización de materiales de estudio personales y recopilación de ideas
> - Práctica de desarrollo frontend e investigación sobre extracción de datos web
> - Aprendizaje sobre estructuras de metadatos multimedia
> - Archivado de contenido público con permiso explícito de los titulares de derechos de autor

⚠️ **Aviso importante**: Esta herramienta solo funciona con **contenido accesible públicamente**. No está diseñada ni habilitada para acceder a contenido privado, contenido que requiera inicio de sesión o cualquier contenido con restricciones de acceso.

---

## ✨ Características Principales

- 🔗 **Reconocimiento Inteligente de Enlaces Públicos**: Detecta automáticamente URLs de contenido público de Naver (blog.naver.com, tv.naver.com, post.naver.com, etc.)
- 🎬 **Soporte Multi-formato**: Extrae metadatos para videos, imágenes, audios y otros archivos multimedia publicamente accesibles (el contenido debe estar configurado con visibilidad pública)
- 📐 **Visualización de Información Básica**: Muestra tipo de medio, tamaño de archivo, timestamp de carga, información del autor y otros metadatos publicamente disponibles
- 📱 **Diseño Totalmente Responsivo**: Experiencia de usuario optimizada para escritorio, tablet y dispositivos móviles
- ⚡ **Arquitectura Priorizando el Lado del Cliente**: La lógica principal de análisis se ejecuta en el navegador, reduciendo la dependencia del servidor y mejorando la velocidad de respuesta
- 🔐 **Diseño Respetuoso con la Privacidad**: No registra las URLs enviadas, no almacena resultados de análisis ni recopila datos personales o información de cuenta de usuarios

---

## 🚀 Guía de Inicio Rápido

1. Abra la plataforma Naver (versión web o aplicación) y localice el **contenido público** que desea consultar
2. Copie la URL de la página desde la barra de direcciones de su navegador (ejemplo: `https://blog.naver.com/username/123456789` o `https://tv.naver.com/v/12345678`)
3. Pegue el enlace en el campo de entrada de esta herramienta y haga clic en el botón "Analizar"
4. El sistema extraerá los metadatos públicamente disponibles y mostrará la información de recursos accesibles
5. Seleccione el recurso preferido, luego haga clic derecho en el enlace y elija "Guardar enlace como..." para descargar localmente

> 💡 Consejos de uso:
> - Verifique siempre que el contenido objetivo esté configurado con visibilidad "Pública"
> - Si el análisis falla, intente actualizar la página o verificar su conexión de red
> - Con fines de aprendizaje, considere usar las Herramientas para Desarrolladores del navegador (F12 → Network → Fetch/XHR) junto con esta herramienta

---

## ⚠️ Cumplimiento Normativo y Descargo de Responsabilidad (Lea Detenidamente)

Este proyecto opera bajo los principios de "neutralidad técnica" y "cumplimiento legal". Por favor, revise y acepte lo siguiente antes de usar:

### ✅ Prácticas Recomendadas
- Analice únicamente **contenido público** al que tenga acceso legítimo
- Utilice los recursos extraídos estrictamente para **aprendizaje personal, investigación o referencia privada**
- Obtenga permiso explícito por escrito de los titulares de derechos de autor antes de redistribuir, crear obras derivadas o usar con fines comerciales
- Siempre acredite a los creadores originales e indique claramente la atribución de fuentes en sus proyectos

### ❌ Actividades Prohibidas
- Intentar acceder o analizar contenido privado, contenido que requiera autenticación o recursos con restricciones de acceso
- Usar esta herramienta para scraping comercial, servicios de agregación de datos o generación de ingresos publicitarios
- Enviar solicitudes automatizadas de alta frecuencia, tráfico de bots o cualquier actividad que pueda interrumpir los servicios de Naver
- Eliminar, alterar u ocultar marcas de agua, avisos de derechos de autor o metadatos incrustados
- Utilizar esta herramienta para acceder, distribuir o propagar contenido que viole la privacidad, leyes o derechos de propiedad intelectual

> 📜 Aviso Legal:
> El uso de esta herramienta debe cumplir con las leyes de derechos de autor aplicables, regulaciones de protección de datos, así como los [Términos de Servicio](https://terms.naver.com/termOfService.naver) y la [Política de Privacidad](https://terms.naver.com/privacy.naver) de Naver.
> Los desarrolladores no asumen responsabilidad alguna por problemas legales, daños o pérdidas que surjan del uso indebido de esta herramienta por parte de los usuarios finales.

---

## 🛠 Notas de Implementación Técnica (Para Desarrolladores)

> Los usuarios generales pueden omitir esta sección

### Visión General de la Arquitectura
```
Navegador del Usuario → Módulo de Análisis en Cliente → Página Pública de Naver / Interfaz OEmbed → Extracción de Datos Estructurados → Renderizado de Resultados
```

### Enfoques Técnicos Clave
- Utiliza la API `fetch` con configuración apropiada de proxy CORS para recuperar metadatos de páginas públicas
- Analiza etiquetas Open Graph (`og:video`, `og:image`, `og:title`, etc.) para el descubrimiento de recursos
- Aprovecha datos estructurados (JSON-LD / Microdata) de las páginas de vista previa para complementar información multimedia
- Implementa validación dual mediante patrones regex + análisis DOM para un reconocimiento robusto de enlaces

### Guía de Auto-alojamiento (Referencia)
```bash
# 1. Clonar el repositorio (ejemplo)
git clone https://github.com/yourname/naver-downloader-sp.git

# 2. Desplegar archivos estáticos (se recomienda HTTPS)
#    - Vercel / Netlify / Cloudflare Pages (configuración sencilla, recomendado)
#    - Nginx + certificado Let's Encrypt (opción auto-alojada)

# 3. Ejemplo de configuración de encabezados de seguridad (Nginx)
add_header Content-Security-Policy "default-src 'self'; script-src 'self' 'unsafe-inline';";
add_header X-Content-Type-Options "nosniff";
add_header Referrer-Policy "strict-origin-when-cross-origin";
add_header X-Frame-Options "DENY";
```

> 🔐 Mejores Prácticas para Implementación en Producción:
> - Habilite siempre HTTPS para prevenir ataques de tipo man-in-the-middle
> - Implemente limitación de tasa (rate limiting) para prevenir abusos y solicitudes excesivas
> - Evite exponer lógica de análisis sensible que pueda ser mal utilizada
> - Revise y actualice regularmente las dependencias para aplicar parches de seguridad

---

## 🤝 Cómo Contribuir

¡Damos la bienvenida a contribuciones de la comunidad para ayudar a mejorar este proyecto educativo!

| Tipo de Contribución | Ejemplos |
|---------------------|----------|
| 🐛 Reporte de Errores | Envíe Issues con pasos detallados: URL + información del navegador + pasos de reproducción |
| 💡 Sugerencias de Funcionalidades | Comparta ideas constructivas para mejoras de UX, accesibilidad o nuevas características educativas |
| 🌍 Ayuda con Traducciones | Asista con la traducción de texto de la interfaz a idiomas adicionales |
| 📚 Documentación | Agregue ejemplos de uso, diagramas técnicos o guías de cumplimiento normativo |

> Este proyecto se publica bajo la [Licencia MIT](./LICENSE). Fomentamos el uso libre y la modificación con fines educativos y de investigación. Para consultas sobre personalización comercial, por favor contáctenos a través de canales separados.

---

## ❓ Preguntas Frecuentes (FAQ)

**P: ¿Por qué aparece el mensaje "No se pudo obtener el contenido"?**  
R: Posibles razones: ① El enlace apunta a contenido privado o que requiere autenticación ② El contenido ha sido eliminado o configurado como "Solo para miembros" ③ Naver cambió temporalmente la estructura de la página ④ Restricciones de red o problemas de CORS. Solución: Verifique el estado público → Pruebe con otra red → Espere e intente nuevamente.

**P: ¿El video/imagen descargado contiene marcas de agua?**  
R: Esta herramienta devuelve las URLs de recursos originales proporcionadas por la infraestructura oficial de Naver. La presencia de marcas de agua depende completamente de la configuración del usuario que subió el contenido. Esta herramienta no añade, elimina ni modifica ninguna marca de agua o marca incrustada.

**P: ¿Se admite el procesamiento por lotes para historial de contenido de Naver Blog/TV?**  
R: La versión actual se enfoca en el análisis de contenido único para priorizar la estabilidad y el cumplimiento normativo. Para operaciones por lotes, por favor asegúrese primero de que su caso de uso se alinee con los [Términos de Servicio](https://terms.naver.com/termOfService.naver) de Naver en cuanto a límites de tasa y uso de datos.

**P: ¿Esta herramienta recopila mis datos de uso o información de cuenta de Naver?**  
R: No. Este es un proyecto frontend estático puro sin registro en backend, scripts de análisis ni seguimiento basado en cookies. Todo el procesamiento ocurre localmente dentro de su sesión de navegador, y no se requiere ningún inicio de sesión.

**P: ¿Puede analizar publicaciones privadas de Naver Cafe o contenido de conversaciones personales?**  
R: No. Esta herramienta soporta exclusivamente **enlaces de páginas públicas**. El análisis de publicaciones privadas, contenido interno de Cafe o recursos que requieran inicio de sesión no está técnicamente soportado y es éticamente desaconsejado. Esto refleja nuestro compromiso fundamental con la privacidad del usuario y el cumplimiento del producto.

---

## 🌱 Nuestra Filosofía

> La tecnología en sí misma es neutral. Lo que importa es la *intención* y la *responsabilidad* de quienes la utilizan.

Animamos a desarrolladores y usuarios a adoptar estos valores:

- 🔬 Buscar una comprensión más profunda de las tecnologías web a través de la curiosidad y el aprendizaje ético
- 🤲 Respetar los derechos de los creadores y la privacidad de los usuarios atribuyendo adecuadamente las fuentes y solicitando permisos
- 🌍 Contribuir a un ecosistema digital saludable que equilibre la innovación con la preservación cultural
- ⚖️ Mantener el equilibrio entre exploración técnica y cumplimiento legal, practicando un desarrollo responsable

Juntos, fomentemos un ciclo positivo de creación, intercambio y uso responsable de la tecnología ✨

---

## 📄 Licencia

Este proyecto se distribuye bajo la [Licencia MIT](./LICENSE).

```
Copyright (c) 2026 Naver Media Analyzer Project

Se concede permiso, de forma gratuita, a cualquier persona que obtenga una copia
de este software y los archivos de documentación asociados (el "Software"), para usar,
copiar, modificar, fusionar, publicar, distribuir, sublicenciar y/o vender
copias del Software, y permitir a las personas a quienes se les proporcione el
Software hacerlo, sujeto a las siguientes condiciones:

El aviso de derechos de autor anterior y este aviso de permiso se incluirán en todas
las copias o partes sustanciales del Software.

EL SOFTWARE SE PROPORCIONA "TAL CUAL", SIN GARANTÍA DE NINGÚN TIPO, EXPRESA O
IMPLÍCITA, INCLUYENDO PERO NO LIMITADO A LAS GARANTÍAS DE COMERCIABILIDAD,
IDONEIDAD PARA UN PROPÓSITO PARTICULAR Y NO INFRACCIÓN. EN NINGÚN CASO LOS
AUTORES O TITULARES DE LOS DERECHOS DE AUTOR SERÁN RESPONSABLES DE NINGUNA
RECLAMACIÓN, DAÑOS U OTRA RESPONSABILIDAD, YA SEA EN UNA ACCIÓN DE CONTRATO,
AGRAVIO O DE OTRO TIPO, QUE SURJA DE, FUERA DE O EN CONEXIÓN CON EL SOFTWARE
O EL USO U OTROS TRATOS EN EL SOFTWARE.
```

---

*📅 Última Actualización: Mayo 2026*  
*🔖 Versión: v1.2.0-es (Optimización frontend / Soporte i18n mejorado / Documentación de cumplimiento reforzada)*