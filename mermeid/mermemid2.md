``````mermaid
classDiagram
%% Definir los paquetes para agrupar las clases
    class Usuario {
        - id: String
        - nombre: String
        - correo: String
        - rol: Rol
    }

    class Rol {
        - id: String
        - nombre: String
    }

    class Sena {
        - id: String
        - nombre: String
        - descripcion: String
        - videoUrl: String
        - usuarioId: String  %% Referencia al usuario que creó la seña
    }

    class Actividades {
        + login(): void
        + autenticarCredenciales(): void
        + iniciarApp(): void
    }

    class TareasUsuario {
        + iniciarApp(): void
        + login(): void
        + autenticarCredenciales(): void
    }

    class ActividadesUsuario {
        - senas: List<Sena>
        + capturaSenaAIdentificar(): void
        + capturaSenaMuestra(): void
        + verInformacionSena(): void
        + consultarUsuariosDestacados(): void
        + actualizarInformacionPerfil(): void
        + consultarInformacionPerfil(): void
    }

    class ActividadesAdmin {
        + registrarSenaBase(Sena sena): void
        + registrarInformacionSenaDLM(): void
    }

    class ActividadesAlgoritmo {
        + reconocerSena(Sena sena): void
    }

%% Relaciones entre las clases
    Usuario -- Rol : tiene
    Usuario --> TareasUsuario : "Realiza"
    TareasUsuario --> Actividades : "Incluye" %% Herencia de las actividades comunes
    TareasUsuario --> ActividadesUsuario : "Incluye"
    TareasUsuario --> ActividadesAdmin : "Opcional para rol admin"
    ActividadesUsuario --> Sena : "captura"
    ActividadesUsuario --> Sena : "ver"
    ActividadesAdmin --> Sena : "registra"
    ActividadesAlgoritmo --> Sena : "reconoce"

%% Definir que el rol determina las actividades disponibles
    Rol --> ActividadesUsuario : "Asigna acceso"
    Rol --> ActividadesAdmin : "Asigna acceso"

%% Herencia de Actividades para Admin y Usuario
    ActividadesUsuario --|> Actividades : "Hereda"
    ActividadesAdmin --|> Actividades : "Hereda"

``````