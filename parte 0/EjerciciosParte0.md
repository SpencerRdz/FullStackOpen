# Diagramas de la Aplicación de Notas

## 0.4: Creación de una nueva nota en la versión clásica

```mermaid
sequenceDiagram
    participant usuario
    participant navegador
    participant servidor

    usuario->>navegador: Escribe nota y hace clic en "Save"
    navegador->>servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate servidor
    servidor-->>navegador: Redirige a /notes
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate servidor
    servidor-->>navegador: HTML document
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: JSON actualizado con la nueva nota
    deactivate servidor
```

## 0.5: Carga de la aplicación en la versión SPA
```mermaid
sequenceDiagram
    participant navegador
    participant servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate servidor
    servidor-->>navegador: HTML minimalista
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate servidor
    servidor-->>navegador: JavaScript SPA
    deactivate servidor

    navegador->>servidor: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate servidor
    servidor-->>navegador: JSON con notas existentes
    deactivate servidor

    Note right of navegador: La aplicación SPA renderiza las notas sin recargar la página
```

## 0.6: Creación de una nueva nota en la versión SPA
```mermaid
sequenceDiagram
    participant usuario
    participant navegador
    participant servidor

    usuario->>navegador: Escribe nota y hace clic en "Save"
    navegador->>servidor: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate servidor
    servidor-->>navegador: Confirma recepción de la nueva nota
    deactivate servidor

    navegador->>navegador: Actualiza la lista de notas sin recargar la página
```

