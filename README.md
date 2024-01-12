def process_shapefiles1(self, diretorio_raiz):
    id_atual = 1  # Inicia o contador de ID
    local_pc = _determinar_local_pc()
    for root, dirs, files in os.walk(diretorio_raiz):
        for arquivo_ou_diretorio in files:
            caminho_completo = Path(root) / arquivo_ou_diretorio
            extensao = caminho_completo.suffix.lower()
            nome = caminho_completo.stem
            __pasta = ShapeProject()
            pasta = __pasta._modificar_nome_pasta(nome)
            destino = Path(local_pc, pasta, caminho_completo.name)
            # destino.parent.mkdir(parents=True, exist_ok=True)  # Comentado para evitar criação de diretórios
            # shutil.copy(caminho_completo, destino)  # Comentado para evitar cópia de arquivos
            __origem__destino = ShapeProject()
            origem = __origem__destino._normalizar_caminho(caminho_completo)
            destino = __origem__destino._normalizar_caminho(destino)
            if extensao == ".shp":
                nome_sem_extensao = re.sub(r'\.shp$', '', nome)
                origem_sem_nome_arquivo = re.sub(r'/[^/]+\.shp$', '/', origem)
                origem_sem_parte_especifica = re.sub(r'^//nas\.ibge\.gov\.br/DGC-ACERVO-CCAR2/CONVERSAO_DIGITAL/CCAR_PRODUTOS_VETOR/Arquivos_Shape/CCAR_PRODUTOS_VETOR/', '', origem_sem_nome_arquivo)
                destino_sem_nome_arquivo = re.sub(r'/[^/]+\.shp$', '/', destino)
                latitude, longitude = LatitudeLongitude()._extract_lat_long(caminho_completo)
                Crud().insert_data(nome_sem_extensao, origem_sem_parte_especifica, destino_sem_nome_arquivo, latitude, longitude)
                print(f"\r{id_atual} | {nome_sem_extensao}.shp", end='')
                id_atual += 1  # Incrementa o ID para a próxima iteração
    print()


## Nest JS Tutorials 
https://www.youtube.com/watch?v=8d75-sTi4UI&list=PLIGDNOJWiL1_AhUGgmwz7RhyXwX5aVLj4

<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo_text.svg" width="320" alt="Nest Logo" /></a>
</p>



[travis-image]: https://api.travis-ci.org/nestjs/nest.svg?branch=master
[travis-url]: https://travis-ci.org/nestjs/nest
[linux-image]: https://img.shields.io/travis/nestjs/nest/master.svg?label=linux
[linux-url]: https://travis-ci.org/nestjs/nest
  
  <p align="center">A progressive <a href="http://nodejs.org" target="blank">Node.js</a> framework for building efficient and scalable server-side applications, heavily inspired by <a href="https://angular.io" target="blank">Angular</a>.</p>
    <p align="center">
<a href="https://www.npmjs.com/~nestjscore"><img src="https://img.shields.io/npm/v/@nestjs/core.svg" alt="NPM Version" /></a>
<a href="https://www.npmjs.com/~nestjscore"><img src="https://img.shields.io/npm/l/@nestjs/core.svg" alt="Package License" /></a>
<a href="https://www.npmjs.com/~nestjscore"><img src="https://img.shields.io/npm/dm/@nestjs/core.svg" alt="NPM Downloads" /></a>
<a href="https://travis-ci.org/nestjs/nest"><img src="https://api.travis-ci.org/nestjs/nest.svg?branch=master" alt="Travis" /></a>
<a href="https://travis-ci.org/nestjs/nest"><img src="https://img.shields.io/travis/nestjs/nest/master.svg?label=linux" alt="Linux" /></a>
<a href="https://coveralls.io/github/nestjs/nest?branch=master"><img src="https://coveralls.io/repos/github/nestjs/nest/badge.svg?branch=master#5" alt="Coverage" /></a>
<a href="https://gitter.im/nestjs/nestjs?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=body_badge"><img src="https://badges.gitter.im/nestjs/nestjs.svg" alt="Gitter" /></a>
<a href="https://opencollective.com/nest#backer"><img src="https://opencollective.com/nest/backers/badge.svg" alt="Backers on Open Collective" /></a>
<a href="https://opencollective.com/nest#sponsor"><img src="https://opencollective.com/nest/sponsors/badge.svg" alt="Sponsors on Open Collective" /></a>
  <a href="https://paypal.me/kamilmysliwiec"><img src="https://img.shields.io/badge/Donate-PayPal-dc3d53.svg"/></a>
  <a href="https://twitter.com/nestframework"><img src="https://img.shields.io/twitter/follow/nestframework.svg?style=social&label=Follow"></a>
</p>
  <!--[![Backers on Open Collective](https://opencollective.com/nest/backers/badge.svg)](https://opencollective.com/nest#backer)
  [![Sponsors on Open Collective](https://opencollective.com/nest/sponsors/badge.svg)](https://opencollective.com/nest#sponsor)-->

## Description

[Nest](https://github.com/nestjs/nest) framework TypeScript starter repository.

## Installation

```bash
$ cp env.example .env
docker-compose build
docker-compose up
```
