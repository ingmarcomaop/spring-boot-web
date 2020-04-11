Si no se indica el metodo se entiende que es GET
Tambien puede llamarse como @GetMapping y ya se sabe que es un
request method del tipo GET
	
@GetMapping("/index") si no hay mas parametros por defecto toma
el parametro value, en este caso, value=/index
	
Para mapear el metodo get a mas rutas se hace {"/index", "/", "/home"}
A una sola ruta seria value="/index"


Al crear un html file la siguiente line se crea utomáticamente:
<meta charset="UTF-8">
Pero, al usar Thymeleaf sale error. Se debe cerrar la llave así:
<meta charset="UTF-8" />

Si le doy click derecho al archivo index.html (Properties) creado y luego 
en "Resource" coincidir UTF-8 para que no genere conflictos. Si se va a 
cambiar, se debe cambiar en el archivo <meta charset="UTF-8" /> y en la
confuguración tambien.

Para importar un titulo creado con Thymeleaf en el html seria:

<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
<meta charset="UTF-8" />
<title th:text="${titulo}"></title>
</head>
<body>

<h1 th:text="${titulo}"></h1>

</body>
</html>

Donde, ${titulo} sale de el controlador en la parte:
model.addAttribute("titulo", "Hola Spring Framework");
Lo anterior fue usando Model. Pero tambien, se puede hacer utilizando
ModelMap. Solo que ModelMap es una clase que hereda el metodo
LinkedHashMap<String, Object>
Pero, ambas dan lo mismo.

Lo anterior tambien se puede hacer con Map, y en controlador quedaría:

public String index(Map<String, Object> map) {
		
		map.put("titulo", "Hola Spring Framework");
		return "index";
	}

Otra forma:

public ModelAndView index(ModelAndView mv) {
		
		mv.addObject("titulo", "Hola Spring Framework");
		mv.setViewName("index");
		return mv;
	}
	
Model es una implementación que permite pasar datos a la vista.
	
	
	





















