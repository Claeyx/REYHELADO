classDiagram
    namespace con_flyweight {
        class Gunter {
            - String tipo
            - String sonido
            + Gunter(String tipo)
            + hacerSonido(int x, int y) void
            + getTipo() String
        }

        class PosicionGunter {
            - int x
            - int y
            - Gunter gunter
            + PosicionGunter(int x, int y, Gunter gunter)
            + activar() void
        }

        class FabricaGunter {
            - Map~String, Gunter~ pool
            + obtenerGunter(String tipo) Gunter
            + getCantidadObjetos() int
        }

        class MainConFlyweight {
            + main(String[] args) void
        }
    }

    namespace sin_flyweight {
        class GunterCompleto {
            - String tipo
            - String sonido
            - int x
            - int y
            + GunterCompleto(String tipo, int x, int y)
            + activar() void
        }

        class MainSinFlyweight {
            + main(String[] args) void
        }
    }

    PosicionGunter --> Gunter : referencia (intrínseco)
    FabricaGunter --> Gunter : gestiona pool
    MainConFlyweight ..> FabricaGunter : solicita objetos
    MainConFlyweight ..> PosicionGunter : crea lista de 100,000
    MainSinFlyweight ..> GunterCompleto : crea 100,000 objetos
