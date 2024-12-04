``````mermaid
classDiagram
%% Definir los paquetes para agrupar las clases
class Usuario{
- id: String
- nombre: String
- correo: String
- rol: Rol
}

    class Rol {
        - id: String
        - nombre: String
    }

    class Seña {
        - id: String
        - nombre: String
        - descripcion: String
        - videoUrl: String
        - usuarioId: String  %% Referencia al usuario que creó la seña
    }


    class Session {
        + iniciarApp(): void
        + login(): void
        + autenticarCredenciales(): void
    }

    class Señante {
        - señas: List<Seña>
        + capturaSeñaAIdentificar(): void
        + capturaSeñaMuestra(): void
        + verInformacionSeña(): void
        + consultarUsuariosDestacados(): void
        + actualizarInformacionPerfil(): void
        + consultarInformacionPerfil(): void
    }

    class Administrador {
        + registrarSeñaBase(Seña seña): void
        + registrarInformacionSeñaDLM(): void
    }

    class ActividadesAlgoritmo {
        + reconocerSeña(Seña seña): void
    }

    %% Relaciones entre las clases
    Usuario -- Rol : tiene
    Usuario --> Session : "Realiza"
    Session --> Señante : "Incluye"
    Session --> Administrador : "Opcional para rol admin"
    Señante --> Seña : "captura"
    Señante --> Seña : "ver"
    Administrador --> Seña : "registra"
    ActividadesAlgoritmo --> Seña : "reconoce"

    %% Definir que el rol determina las actividades disponibles
    Rol --> Señante : "Asigna acceso"
    Rol --> Administrador : "Asigna acceso"
``````