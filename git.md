# Add new credential and erase old credential
```
git config --global user.email '<git-commit-address>'
git config --global --unset credential.helper
```
# To checkout to remote branch, you will need to fetch the contents of the branch using 
```
git fetch --all
```
first. Then use the same command
```
git checkout RemoteBranchName
```
# Para configurar GitLab con SSH en Ubuntu, sigue estos pasos:

1. **Generar un nuevo par de claves SSH (si es necesario):** Si aún no tienes un par de claves SSH en tu sistema, puedes generar uno con el siguiente comando:

   ```bash
   ssh-keygen -t rsa -b 4096 -C "tu_correo@ejemplo.com"
   ```

   Esto generará un nuevo par de claves SSH en el directorio `~/.ssh`. Reemplaza `"tu_correo@ejemplo.com"` con tu dirección de correo electrónico.

2. **Iniciar el agente SSH:** El agente SSH te ayudará a gestionar tus claves SSH. Inicia el agente SSH con el siguiente comando:

   ```bash
   eval "$(ssh-agent -s)"
   ```

3. **Agregar tu clave privada al agente SSH:** Agrega tu clave privada al agente SSH con el siguiente comando:

   ```bash
   ssh-add ~/.ssh/id_rsa
   ```

   Si has generado tus claves con un nombre diferente, asegúrate de reemplazar `id_rsa` con el nombre de tu clave privada.

4. **Copiar la clave pública SSH al portapapeles:** Copia tu clave pública SSH al portapapeles para agregarla a tu cuenta de GitLab. Utiliza el siguiente comando:

   ```bash
   sudo apt-get install xclip   # Instala xclip si no está instalado
   xclip -sel clip < ~/.ssh/id_rsa.pub
   ```

   Esto copiará la clave pública SSH al portapapeles.

5. **Ingresar a tu cuenta de GitLab:**

   - Abre tu navegador web y accede a tu cuenta de GitLab en línea en [https://gitlab.com](https://gitlab.com) u la URL de tu instancia de GitLab si estás utilizando una instalación local.

6. **Agregar la clave pública SSH a tu cuenta de GitLab:**

   - Haz clic en tu avatar de perfil en la esquina superior derecha.
   - Selecciona "Settings" (Configuración) en el menú desplegable.
   - En la barra lateral izquierda, selecciona "SSH Keys" (Claves SSH).
   - Haz clic en el botón "Add SSH Key" (Agregar clave SSH).
   - Dale a la clave un nombre descriptivo en el campo "Key Title".
   - En el campo "Key", pega la clave pública SSH que copiaste en el paso 4.
   - Haz clic en el botón "Add key" (Agregar clave).

7. **Probar la conexión SSH:** Puedes probar si la configuración de SSH funciona correctamente ejecutando el siguiente comando:

   ```bash
   ssh -T git@gitlab.com
   ```

   Si estás utilizando una instancia local de GitLab, reemplaza `gitlab.com` con la URL correspondiente. Deberías recibir un mensaje de confirmación de que la autenticación fue exitosa.

Ahora, GitLab en tu sistema Ubuntu debería estar configurado para usar SSH para la autenticación, lo que te permitirá clonar, empujar y tirar repositorios de GitLab sin necesidad de ingresar tu contraseña cada vez.
