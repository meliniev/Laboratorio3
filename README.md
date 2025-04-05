# Laboratorio3

//Ejercicio 03

class Usuario {
  String nombre;
  String email;
  String contrasena;

  Usuario(this.nombre, this.email, this.contrasena);
}

mixin Autenticacion {
  void iniciarSesion(String email) {
    print("Iniciando sesión con email: $email");
  }
}

class UsuarioAutenticado extends Usuario with Autenticacion {
  UsuarioAutenticado(String nombre, String email, String contrasena) : super(nombre, email, contrasena);
}

void main() {
  var usuario = UsuarioAutenticado("Melanie", "melanie@gmail.com", "123456");
  usuario.iniciarSesion(usuario.email); 
}



//Ejercicio 05
class Votante {
  String nombre;
  int edad;
  bool haVotado;

  Votante(this.nombre, this.edad, {this.haVotado = false});
}

mixin ValidacionVoto {
  void validarVoto() {
    final votante = this as Votante;
    if (votante.edad >= 18) {
      print("${votante.nombre} puede votar.");
    } else {
      print("${votante.nombre} no cumple la edad mínima.");
    }
  }
}

class VotanteValido extends Votante with ValidacionVoto {
  VotanteValido(String nombre, int edad) : super(nombre, edad);
}

void main() {
  var votante1 = VotanteValido("María", 25);
  votante1.validarVoto();

  var votante2 = VotanteValido("Luis", 16);
  votante2.validarVoto();  
}
