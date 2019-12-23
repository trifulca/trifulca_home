Este repositorio es solo un redireccionador para enviar a los
usuarios directo a la web de trifulca (que está en subdominio).

http://trifulca.com.ar

Este repositorio no tiene configurado ningún tipo de integración
contínua o deploy automático, si queres hacer un deploy a dokku
deberías invocar algo como esto:

```
git remote add dokku dokku@trifulca.com.ar:trifulca_home
git remote add dokku2 dokku@trifulca.com.ar:00-default

git push dokku master -f
git push dokku2 master -f
```

Una de las aplicaciones (trifulca\_home) se encarga de cargarse
cuando no se incluye un dominio (por ejemplo trifulca.com.ar)
ya que tenemos el dominio apuntando directamente ahí:


```
# dokku domains:report trifulca_home

=====> trifulca_home domains information
       Domains app enabled:           true
       Domains app vhosts:            trifulca.com.ar
       Domains global enabled:        true
       Domains global vhosts:         trifulca.com.ar
```

y la otra aplicación con nombre 00-default es la que dokku va
a invocar cada vez que se intente acceder a un subdominio incorrecto
como "http://demo.trifulca.com.ar"
