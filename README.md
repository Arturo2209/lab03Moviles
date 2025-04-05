# lab03Moviles
// Ejercicio 1

class Usuario {
  String nombre;
  String email;
  String contrasena;
  
  Usuario(this.nombre, this.email, this.contrasena);
}

mixin Autenticacion {
  void iniciarSesion() {
    print("Iniciando sesión...");
  }
}

class UsuarioAutenticado extends Usuario with Autenticacion {
  UsuarioAutenticado(String nombre, String email, String contrasena)
      : super(nombre, email, contrasena);
}

void main2() {
  var usuario = UsuarioAutenticado('Juan', 'juan@ejemplo.com', 'contraseña123');
  
  usuario.iniciarSesion();
}

// Ejercicio 5

class Votante {
  String nombre;
  int edad;
  bool haVotado;
  
  Votante(this.nombre, this.edad, this.haVotado);
}

mixin ValidacionVoto {
  void validarVoto(Votante votante) {
    if (votante.edad >= 18 && !votante.haVotado) {
      print("${votante.nombre} es elegible para votar.");
    } else if (votante.edad < 18) {
      print("${votante.nombre} no es elegible para votar porque es menor de edad.");
    } else {
      print("${votante.nombre} ya ha votado.");
    }
  }
}

class VotanteValido extends Votante with ValidacionVoto {
  VotanteValido(String nombre, int edad, bool haVotado)
      : super(nombre, edad, haVotado);
}

void main() {
  
  var votante1 = VotanteValido('Juan', 20, false);
  var votante2 = VotanteValido('Ana', 17, false);
  var votante3 = VotanteValido('Luis', 25, true);

  
  votante1.validarVoto(votante1); 
  votante2.validarVoto(votante2); 
  votante3.validarVoto(votante3); 
}
