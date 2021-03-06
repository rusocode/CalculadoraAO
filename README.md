## CalculadoraAO [![Download CalculadoraAO](https://sourceforge.net/sflogo.php?type=10&group_id=3243176)](https://sourceforge.net/p/calculadoraao/files/)
Calculadora multiplataforma basada en **Argentum Online** que calcula el porcentaje de experiencia que otorga cada NPC, la cantidad de NPCs a matar y el oro total a conseguir.

![](screenshot.png)

[![Download CalculadoraAO](https://a.fsdn.com/con/app/sf-download-button)](https://sourceforge.net/projects/calculadoraao/files/latest/download)

### Características
- Calcula el porcentaje de experiencia que otorga cada NPC.
- Calcula la cantidad total de NPCs necesarios para pasar de nivel.
- Calcula la cantidad total de oro a conseguir.
- Manipulacion de datos a traves de archivos **.dat** (niveles, npcs, oro, etc.), siendo aplicable a cualquier server.
- Sistema de ajustes para [ImperiumAO](https://www.imperiumao.com.ar/)
	- Grupos *_Los renegados pierden un 10% de la experiencia total al formar grupos_.
	- Evento de experiencia x2.
	- Evento de oro x2.
	- Scroll de experiencia +10%.
	- Scroll de experiencia +25%.
	- Bonificador premium (+10% de experiencia y +5% de oro).
- Interfaz gráfica de usuario administrada por la librería [MigLayout](https://github.com/mikaelgrev/miglayout).

_Consulte [CHANGELOG.md](https://github.com/rusocode/CalculadoraAO/blob/master/CHANGELOG.md) para mas detalles_

### Getting started

Para el desarrollo sugerimos:
- Eclipse o IntellIJ IDEA
- JDK 8

Para ejecutar:
- **[JRE 8](https://www.java.com/es/download/)**

#### Gradle (Eclipse)
1. Clonar el repositorio.
2. Dentro de Eclipse: *File* > *Import* > *Gradle* > *Existing Gradle Project*.
3. Buscan el proyecto en el sistema y finalizan.

#### Maven
```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<!-- Definicion del artefacto -->
	<groupId>com.silentsoft.calculadoraao</groupId>
	<artifactId>CalculadoraAO</artifactId>
	<version></version> 
	<packaging>jar</packaging>
	<name>CalculadoraAO</name>
	<description>Calculadora basada en ImperiumAO</description>
	<url>https://github.com/rusocode/CalculadoraAO</url>

	<!-- Propiedades del compilador -->
	<properties>
		<project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
		<maven.compiler.source>1.8</maven.compiler.source>
		<maven.compiler.target>1.8</maven.compiler.target>
	</properties>

	<licenses>
		<license>
			<name>GNU GPL v3.0</name>
			<url>https://www.gnu.org/licenses/</url>
			<distribution>repo</distribution>
		</license>
	</licenses>

	<developers>
		<developer>
			<id>Ru$o</id>
			<name>Juan Debenedetti</name>
			<email>juandebenedetti94@gmail.com</email>
			<roles>
				<role>owner</role>
				<role>developer</role>
			</roles>
		</developer>
	</developers>

	<dependencies>
		<!-- https://search.maven.org/artifact/com.miglayout/miglayout/3.7.4/jar -->
		<dependency>
			<groupId>com.miglayout</groupId>
			<artifactId>miglayout</artifactId>
			<version>3.7.4</version>
			<scope>compile</scope>
		</dependency>

		<!-- https://search.maven.org/artifact/org.swinglabs.swingx/swingx-autocomplete/1.6.5-1/jar -->
		<dependency>
			<groupId>org.swinglabs.swingx</groupId>
			<artifactId>swingx-autocomplete</artifactId>
			<version>1.6.5-1</version>
		</dependency>
	</dependencies>

	<!-- Configura maven-compiler-plugin para usar la misma codificacion de 
		caracteres en la que estan codificados los archivos fuente. -->
	<build>
		<plugins>
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-compiler-plugin</artifactId>
				<version>3.8.1</version>
				<configuration>
					<encoding>UTF-8</encoding>
				</configuration>
			</plugin>

			<!-- Plugin para generar el .jar con las dependencias includidas -->
			<plugin>
				<groupId>org.apache.maven.plugins</groupId>
				<artifactId>maven-assembly-plugin</artifactId>
				<version>3.3.0</version>
				<configuration>
					<archive>
						<manifest>
							<mainClass>com.silentsoft.calculadoraao.Main</mainClass> <!-- Indica la clase con el metodo main -->
						</manifest>
					</archive>
					<descriptorRefs>
						<descriptorRef>jar-with-dependencies</descriptorRef>
					</descriptorRefs>
				</configuration>
			</plugin>
		</plugins>
	</build>

</project>
```
_**IMPORTANTE!** Generar el JAR Ejecutable desde [Maven](https://maven.apache.org/download.cgi) y **NO** desde el IDE (solución en [Stack Overflow](https://stackoverflow.com/questions/40024242/how-to-load-resources-from-src-main-resources-in-a-way-that-will-work-both-dire))._
1. Copiar el plugin dentro del archivo pom.xml.
```xml
<!-- Plugin para generar el .jar con las dependencias includidas -->
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-assembly-plugin</artifactId>
	<version>3.3.0</version>
	<configuration>
		<archive>
			<manifest>
				<mainClass>com.silentsoft.Launcher</mainClass> <!-- Indica la clase con el metodo main -->
			</manifest>
		</archive>
		<descriptorRefs>
			<descriptorRef>jar-with-dependencies</descriptorRef>
		</descriptorRefs>
	</configuration>
</plugin>
```
2. Ejecutar `mvn clean compile assembly:single` en consola para generar el .jar dentro de la carpeta target.

### Contacto
juandebenedetti94@gmail.com
