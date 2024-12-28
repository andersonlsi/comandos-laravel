# Comandos para criação de Projetos em Laravel 

Projeto realizado no curso de ERP em Laravel da plataforma MJailton.

<a href="https://laravel.com/" target="_blank">**Acesse a documentação do Laravel aqui**</a>


## Requisitos

* PHP 8.2 ou superior
* Composer
* Node.js 20 ou superior

*Obs:* Caso não tenha os requisitos acima, precisa instalar antes para poder começar um projeto em laravel.


# CRIANDO O PROJETO

## 1 - Criação do Banco
No laravel 10 precisa criar antes de rodar o comando migrate o banco de dados, já no laravel 11 não precisa mais.

## 2 - Criar o projeto com Laravel

### Criar projeto laravel 10
```
composer create-project laravel/laravel my-app "10.0.*" nome_do_seu_projeto
```

### Criar projeto laravel 11
```
omposer create-project --prefer-dist laravel/laravel:^11.0.* nome_do_seu_projeto
```

# CRIANDO UM PROJETO COM BREEZE
Após criar o projeto, execute os comandos abaixo para criar o breeze.

```
composer require laravel/breeze --dev
```
```
php artisan breeze:install
```

# INSTALANDO AS DEPEDENCIAS JAVASCRITP E COMPILANDO OS ATIVOS

```
npm install
```
```
npm run dev
```


# CONFIGURANDO O PROJETO

## Configuração .env
Neste item vamos fazer a Configuração o arquivo **.env**, faça os procedimentos abaixo:

### 1 - Configuração do Nome do Projeto
Abra o arquivo **.env** Configure o Nome do Projeto usando a variável **APP_NAME**

## 2 - Configuração do Banco de Dados
Faça as devidas configurações do Banco de Dados, nas variáveis abaixo:
```
DB_CONNECTION=mysql
DB_HOST=127.0.0.1 // Aqui você configura o servidor do Banco de Dados
DB_PORT=3306 // Aqui você configura a porta do Banco de Dados
DB_DATABASE=nome-banco // Aqui você configura o nome do Banco de Dados
DB_USERNAME=root // Aqui você configura o Nome do Usuário do Banco de Dados
DB_PASSWORD= //Aqui você configura a senha do banco de dados, se vc instalou o Xampp, a senha padrão é vazio
```

## Configuração config/app
Abra o arquivo **config/app** e faça as configurações de **timezone** e **locale**, se não conseguir siga os passos abaixo:

### 1 - timezone
Abra o arquivo **config/app** e procure por **timezone**, em seguida configure de acordo com a sua necessidade, ex: **'timezone' => 'America/Sao_Paulo'**

### 2 - locale
Ainda no arquivo **config/app** Configure o locale de acordo com sua necessidade, ex: **'locale' => 'pt_BR'**

## Tradução do Laravel
Caso você queira fazer a tradução das mensagens do Laravel, siga os passo abaixo:

### 1 - Comando 1
```
composer require lucascudo/laravel-pt-br-localization --dev
```

### 2 - Comando 2
```
php artisan vendor:publish --tag=laravel-pt-br-localization
```

## Criação do Helper
Crie um arquivo de helper para sua aplicação, o helper é importante para você personalizar funções específicas do seu projeto, caso não saiba como fazer siga as orientações abaixo:

### 1 - Criação do Arquivo helpers.php
Crie uma pasta chamada Helper dentro de app e em seguida <a href="https://drive.google.com/file/d/11hChm426c2DiavXsvUj_bVH1xiRCcLeR/view?usp=sharing" target="_blank">**baixe aqui o arquivo**</a> e coloquei dentro desta pasta.

### 2 - Registro no Composer.json
Registre o helper no autoload do composer arquivo **composer.json** dentro de **autoload**

```
"files" : [
   "app/Helper/helpers.php"
 ],
 ```

### 3 - Atualização do Composer
Atualize o composer usando o comando: 

 ```
composer update
 ```

 ## Outros Passos
 Outros comandos de configuração

 ### 1 - Biblioteca de Validação
 Caso ache interessante para seu projeto instale a biblioteca de Validação para o seu projeto, caso não saiba como siga os passos abaixo:

```
composer require laravellegends/pt-br-validator
```

### 2 - Constantes para status
<a href="https://drive.google.com/file/d/1pVtfswF5Ll3vxHKU8VSMcJrN4Ud1f281/view?usp=sharing" target="_blank">**Baixe aqui**</a> o arquivo e coloque dentro da pasta **config**.

### 3 - Arquivo UtilService
Crie a pasta **Service** dentro da pasta **app**, depois dentro da pasta Service crie o arquivo **UltilService.php** e implemente a classe.

```
<?php

namespace App\Service;

class UtilService{
    
}
```
# INSERINDO UM LAYOUT 
Se preferir poderá baixar um layout de sua escolha para criar o projeto.


## 1 - Criando as Views Necessárias
Dentro da Pasta **resources/views** crie **04 arquivos**, sendo eles:

**- cabecalho.blade.php**
**- home.blade.php**
**- menu.blade.php**
**- template.php**

## 2 - Criando o HomeController

### 1 - Comando
```
php artisan make:controller HomeController
```

### 2 - Método Index
```
public function index(){
        return view("home");
    }
```

## 3 - Criando a rota home
```
Route::get('/', [HomeControlller::class, "index"] )->name("home");
```

## 4 - Copiando a pasta inc
Copie a pasta inc (que está no arquivo que foi baixado) para a pasta **resources/views**.

## 5 - Copiando os arquivos de recursos
Dentro da pasta public crie uma pasta chamada assets e dentro dela copie as pastas:

**- componentes**
**- css**
**- img**
**- js**

# FATIANDO LAYOUT - PARTE 01

<a href="https://mjailton.com.br/campus/conteudo/passo/1476/38158/661/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula 01**</a>
<a href="https://mjailton.com.br/campus/conteudo/passo/1476/38163/661/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula 02**</a>

## 1 - Instruções gerais
Para fatiar o layout é importante observar a estrutura html do arquivo index do layout baixado e verificar dentro desta estrutura o que representa a página home, o cabecalho, rodapé, menu, etc. Desta forma, abra o arquivo index do layout que foi baixo e faça os procedimentos abaixo:

- abra o arquivo template.blade.php que está dentro da pasta resources/views

- Copie o conteúdo do arquivo index do layout baixado para o arquivo template.blade.php

-Para que os recursos possam ser visualizados no layout é necessário setá-los, ou seja, informar o caminho completo dos recursos e para isso vamos usar a função asset e informar com caminho completo dos recursos.

- Sete todos os recursos necessários do arquivo template para que possa linkar o css, imagem e js e em seguida rode o projeto.

## 2 - Cabeçalho
Crie um arquivo chamado cabecalho.blade.php dentro da pasta resources/views, em seguida faça os procedimentos abaixo:


- Do arquivo template recorte o conteúdo que você considera fazer parte do cabeçalho do projeto
- Abra o arquivo cabecalho.blade.php e cole o conteúdo recortado
- No arquivo index no local onde estava o conteúdo que foi recortado para o cabecalho faça um include ao arquivo cabecalho

```
<div class="topo d-flex text-end">    
			<a href="" class="mobmenu alt"><i class="fas fa-bars"></i></a>
			<ul class="menu-topo">
				<li class="sub">
									<img src="img/foto.png" class="img-user">
								<span class="text-branco"></span>
					<ul>
						<li><a href="#" class=""><i class="fas fa-lock"></i> Usuário</a> </li>

						<li><a href="">Sair</a></li>
					</ul>
				</li>
			</ul>
		</div>
```

## 3 - Menu
Para configurar o arquivo menu, façamos o seguinte procedimento:

- Crie um arquivo chamado cabecalho.blade.php dentro da pasta **resources/views**:
- no arquivo template recorte o conteúdo que você considera fazer parte do menu do projeto
- Abra o arquivo menu.blade.php e cole o conteúdo recortado
- No arquivo index no local onde estava o conteúdo que foi recortado para o menu faça um include ao arquivo cabecalho

```
 <div class="menu-lateral">
    <a href="" class="logo d-block" style="background:none">
        <img src="img/logomin-zeus.svg">
    </a>
    <div class="logo-text">Projeto Zeus</div>
    <nav class="menuprincipal" id="principal">
        <ul class="menu-ul icones">
            <li><a href="">
                    <svg class="icon" viewBox="0 0 22 20" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M1.25 11L10.204 2.04499C10.644 1.60599 11.356 1.60599 11.795 2.04499L20.75 11M3.5 8.74999V18.875C3.5 19.496 4.004 20 4.625 20H8.75V15.125C8.75 14.504 9.254 14 9.875 14H12.125C12.746 14 13.25 14.504 13.25 15.125V20H17.375C17.996 20 18.5 19.496 18.5 18.875V8.74999M7.25 20H15.5"
                            stroke="#341008" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                    <span>Home</span>
                </a>
            </li>
            <li class="submenu">
                <a href="#">
                    <svg class="icon" viewBox="0 0 20 19" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M11.5 14.875H14.875M14.875 14.875H18.25M14.875 14.875V11.5M14.875 14.875V18.25M4 8.5H6.25C6.84674 8.5 7.41903 8.26295 7.84099 7.84099C8.26295 7.41903 8.5 6.84674 8.5 6.25V4C8.5 3.40326 8.26295 2.83097 7.84099 2.40901C7.41903 1.98705 6.84674 1.75 6.25 1.75H4C3.40326 1.75 2.83097 1.98705 2.40901 2.40901C1.98705 2.83097 1.75 3.40326 1.75 4V6.25C1.75 6.84674 1.98705 7.41903 2.40901 7.84099C2.83097 8.26295 3.40326 8.5 4 8.5ZM4 18.25H6.25C6.84674 18.25 7.41903 18.0129 7.84099 17.591C8.26295 17.169 8.5 16.5967 8.5 16V13.75C8.5 13.1533 8.26295 12.581 7.84099 12.159C7.41903 11.7371 6.84674 11.5 6.25 11.5H4C3.40326 11.5 2.83097 11.7371 2.40901 12.159C1.98705 12.581 1.75 13.1533 1.75 13.75V16C1.75 16.5967 1.98705 17.169 2.40901 17.591C2.83097 18.0129 3.40326 18.25 4 18.25ZM13.75 8.5H16C16.5967 8.5 17.169 8.26295 17.591 7.84099C18.0129 7.41903 18.25 6.84674 18.25 6.25V4C18.25 3.40326 18.0129 2.83097 17.591 2.40901C17.169 1.98705 16.5967 1.75 16 1.75H13.75C13.1533 1.75 12.581 1.98705 12.159 2.40901C11.7371 2.83097 11.5 3.40326 11.5 4V6.25C11.5 6.84674 11.7371 7.41903 12.159 7.84099C12.581 8.26295 13.1533 8.5 13.75 8.5Z"
                            stroke="#341008" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                    <span>Cadastro</span>
                </a>
                <ul>
                    <li class="subcat">
                        <a href="">Tabelas Auxiliares</a>
                        <ul>
                            <li><a href="categoria">Categoria</a></li>
                            <li><a href="unidade">Unidade</a></li>
                            <li><a href="banco">Banco</a></li>
                            <li><a href="tipocontacorrente">Tipo Conta Corrente</a></li>
                            <li><a href="status">Status</a></li>
                            <li><a href="formapagto">Forma Pagto</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Produto</a>
                        <ul>
                            <li><a href="produto">Lista de produto</a></li>
                            <li><a href="produto/create">Cadastro de produto</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Cliente</a>
                        <ul>
                            <li><a href="cliente">Lista de Cliente</a></li>
                            <li><a href="cliente/create">Cadastro de Cliente</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Fornecedor</a>
                        <ul>
                            <li><a href="fornecedor">Lista de Fornecedor</a></li>
                            <li><a href="fornecedor/create">Cadastro de Fornecedor</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Transportadora</a>
                        <ul>
                            <li><a href="transportadora">Lista de Tranpostadora</a></li>
                            <li><a href="transportadora/create">Cadastro de Transportadora</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Vendedor</a>
                        <ul>
                            <li><a href="vendedor">Lista</a></li>
                            <li><a href="vendedor/create">Cadastro de Vendedor</a></li>
                        </ul>
                    </li>

                    <li class="subcat">
                        <a href="">Conta Corrente</a>
                        <ul>
                            <li><a href="contacorrente">Lista de Conta Corrente</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Imagens</a>
                        <ul>
                            <li><a href="imagem">Lista de Imagens</a></li>
                        </ul>
                    </li>

                    <li class="subcat">
                        <a href="">Grade Produto</a>
                        <ul>
                            <li><a href="variacaograde">Lista de Variação</a></li>
                            <li><a href="itemvariacaograde">Item da Variação</a></li>
                        </ul>
                    </li>


                    <li class="subcat">
                        <a href="">Cupom Desconto</a>
                        <ul>
                            <li><a href="cupomdesconto">Lista de Cupom Desconto</a></li>
                        </ul>
                    </li>

                </ul>
            </li>
            
            




            <li class="submenu">
                <a href="#">
                    <svg class="icon" viewBox="0 0 98 91" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M19 19.64V15.25C19 12.2663 20.1853 9.40483 22.295 7.29505C24.4048 5.18527 27.2663 4 30.25 4H67.75C70.7337 4 73.5952 5.18527 75.705 7.29505C77.8147 9.40483 79 12.2663 79 15.25V19.64M19 19.64C20.175 19.225 21.435 19 22.75 19H75.25C76.565 19 77.825 19.225 79 19.64M19 19.64C16.8061 20.4157 14.9066 21.8526 13.5634 23.7528C12.2202 25.653 11.4993 27.923 11.5 30.25V34.64M79 19.64C81.1939 20.4157 83.0933 21.8526 84.4366 23.7528C85.7798 25.653 86.5007 27.923 86.5 30.25V34.64M11.5 34.64C12.675 34.225 13.935 34 15.25 34H82.75C84.0273 33.9985 85.2955 34.215 86.5 34.64M11.5 34.64C7.13 36.185 4 40.35 4 45.25V75.25C4 78.2337 5.18526 81.0952 7.29505 83.205C9.40483 85.3147 12.2663 86.5 15.25 86.5H82.75C85.7337 86.5 88.5952 85.3147 90.705 83.205C92.8147 81.0952 94 78.2337 94 75.25V45.25C94.0007 42.923 93.2798 40.653 91.9366 38.7528C90.5933 36.8526 88.6939 35.4157 86.5 34.64"
                            stroke="white" stroke-width="8" stroke-linecap="round" stroke-linejoin="round"></path>
                    </svg>
                    <span>Estoque</span>
                </a>
                <ul>
                    <li class="subcat">
                        <a href="">Entradas</a>
                        <ul>
                            <li><a href="entrada">Entradas avulsa</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Saídas</a>
                        <ul>
                            <li><a href="saida">Saídas Avulsas</a></li>
                        </ul>
                    </li>
                    <li class="subcat">
                        <a href="">Movimentações</a>
                        <ul>
                            <li><a href="lst-historico-movimento.html">Histórico de movimento</a></li>
                        </ul>
                    </li>

                </ul>
            </li>

                            <li class="submenu">
    <a href="#">
       <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="icon">
  <path stroke-linecap="round" stroke-linejoin="round" d="M19.5 14.25v-2.625a3.375 3.375 0 00-3.375-3.375h-1.5A1.125 1.125 0 0113.5 7.125v-1.5a3.375 3.375 0 00-3.375-3.375H8.25m5.231 13.481L15 17.25m-4.5-15H5.625c-.621 0-1.125.504-1.125 1.125v16.5c0 .621.504 1.125 1.125 1.125h12.75c.621 0 1.125-.504 1.125-1.125V11.25a9 9 0 00-9-9zm3.75 11.625a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z" />
</svg>

        <span>NFE</span>
    </a>
    <ul>
        <li class="subcat">
            <a href="">Emitente</a>
            <ul>
                <li><a href="emitente">Lista de Emitente</a></li>
                <li><a href="emitente/create">Cadastro de Emitente</a></li>
            </ul>
        </li>

        <li class="subcat">
            <a href="">Natureza da Operação</a>
            <ul>
                <li><a href="naturezaoperacao">Lista de Natureza Operação</a></li>
                <li><a href="naturezaoperacao/create">Cadastro de Natureza de Operação</a></li>
            </ul>
        </li>

        <li class="subcat">
            <a href="">Certificado Digital</a>
            <ul>
                <li><a href="certificadodigital">Lista de Certificado Digital</a></li>
                <li><a href="certificadodigital/create">Cadastro de Certificado Digital</a></li>
            </ul>
        </li>
        <li class="subcat">
            <a href="">Notas Fiscais</a>
            <ul>
                <li><a href="notafiscal">Lista de Notas Fiscais</a></li>
                <li><a href="notafiscal/create">Cadastro de Nota Fiscal</a></li>
            </ul>
        </li>


    </ul>
</li>
            
            
            
            
                            <li class="submenu">
    <a href="#">
        <svg class="icon" viewBox="0 0 98 110" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
                d="M4 22.0446H10.4325C12.7995 22.0446 14.8648 23.6364 15.4774 25.9199L17.2549 32.5891M17.2549 32.5891L28.3657 74.2568M17.2549 32.5891C23.2836 32.4201 23.7246 32.5891 30.6863 32.5891H17.2549ZM17.2549 32.5891L23.0777 54.4259L28.3657 74.2568M28.3657 74.2568C24.673 74.2568 21.1316 75.7239 18.5205 78.3349C15.9094 80.946 14.4425 84.4876 14.4425 88.1801H87.5396M28.3657 74.2568H80.4295M28.3657 74.2568C35.3129 74.9785 73.5523 74.1241 80.4295 74.2568M80.4295 74.2568C85.6321 63.5823 90.1757 52.5179 94 41.1287C93.7243 41.945 81.7382 73.0965 80.4295 74.2568ZM48.0903 29.526L62.0136 41.1287M62.0136 41.1287L75.9369 29.526M62.0136 41.1287V9.80136V4M21.4041 102.103C21.4041 103.026 21.0373 103.912 20.3846 104.565C19.7318 105.218 18.8464 105.584 17.9233 105.584C17.0001 105.584 16.1147 105.218 15.462 104.565C14.8092 103.912 14.4425 103.026 14.4425 102.103C14.4425 101.18 14.8092 100.295 15.462 99.6422C16.1147 98.9892 17.0001 98.6225 17.9233 98.6225C18.8464 98.6225 19.7318 98.9892 20.3846 99.6422C21.0373 100.295 21.4041 101.18 21.4041 102.103ZM80.578 102.103C80.578 103.026 80.2113 103.912 79.5583 104.565C78.9058 105.218 78.0203 105.584 77.0972 105.584C76.174 105.584 75.2885 105.218 74.636 104.565C73.983 103.912 73.6163 103.026 73.6163 102.103C73.6163 101.18 73.983 100.295 74.636 99.6422C75.2885 98.9892 76.174 98.6225 77.0972 98.6225C78.0203 98.6225 78.9058 98.9892 79.5583 99.6422C80.2113 100.295 80.578 101.18 80.578 102.103Z"
                stroke="white" stroke-width="8" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
        <span>Vendas</span>
    </a>
    <ul>
        <li class="subcat">
            <a href="">Venda</a>
            <ul>
                <li><a href="venda">Lista de Vendas</a></li>
                <li><a href="venda/create">Cadastro de Venda</a></li>
            </ul>
        </li>


    </ul>
</li>
            
                            <li class="submenu">
    <a href="#">
        <svg class="icon" viewBox="0 0 98 107" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
                d="M68.0147 45.8274V23.0124C68.0147 17.97 66.0116 13.1341 62.4461 9.56862C58.8805 6.00309 54.0446 4 49.0022 4C43.9598 4 39.1239 6.00309 35.5584 9.56862C31.9929 13.1341 29.9898 17.97 29.9898 23.0124V45.8274M87.5645 35.7229L93.9679 96.5627C94.3228 99.9343 91.6864 102.865 88.2946 102.865H9.70985C8.90984 102.866 8.1186 102.698 7.38753 102.373C6.65646 102.048 6.0019 101.573 5.46639 100.979C4.93087 100.385 4.52636 99.6844 4.27915 98.9235C4.03194 98.1627 3.94755 97.3583 4.03146 96.5627L10.4399 35.7229C10.5877 34.3213 11.2492 33.0242 12.2968 32.0814C13.3444 31.1387 14.7039 30.6172 16.1132 30.6174H81.8912C84.8115 30.6174 87.2603 32.8229 87.5645 35.7229ZM31.891 45.8274C31.891 46.3316 31.6907 46.8152 31.3342 47.1718C30.9776 47.5283 30.494 47.7286 29.9898 47.7286C29.4855 47.7286 29.002 47.5283 28.6454 47.1718C28.2889 46.8152 28.0885 46.3316 28.0885 45.8274C28.0885 45.3231 28.2889 44.8395 28.6454 44.483C29.002 44.1264 29.4855 43.9261 29.9898 43.9261C30.494 43.9261 30.9776 44.1264 31.3342 44.483C31.6907 44.8395 31.891 45.3231 31.891 45.8274ZM69.9159 45.8274C69.9159 46.3316 69.7156 46.8152 69.3591 47.1718C69.0025 47.5283 68.5189 47.7286 68.0147 47.7286C67.5104 47.7286 67.0268 47.5283 66.6703 47.1718C66.3137 46.8152 66.1134 46.3316 66.1134 45.8274C66.1134 45.3231 66.3137 44.8395 66.6703 44.483C67.0268 44.1264 67.5104 43.9261 68.0147 43.9261C68.5189 43.9261 69.0025 44.1264 69.3591 44.483C69.7156 44.8395 69.9159 45.3231 69.9159 45.8274Z"
                stroke="white" stroke-width="8" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
        <span>Compras</span>
    </a>
    <ul>
        <li class="subcat">
            <a href="">Compra Manual</a>
            <ul>
                <li><a href="compra">Lista de Compras</a></li>
                <li><a href="compra/create">Nova Compra</a></li>
            </ul>
        </li>
        <li class="subcat">
            <a href="">Importação de XML</a>
            <ul>
                <li><a href="compra">Lista de Compras</a></li>
                <li><a href="compra/create">Nova Compra</a></li>
            </ul>
        </li>

        <li class="subcat">
            <a href="">Manifesto</a>
            <ul>
                <li><a href="compra">Lista de Compras</a></li>
                <li><a href="compra/create">Nova Compra</a></li>
            </ul>
        </li>

        <li class="subcat">
            <a href="">Ordem de Compra</a>
            <ul>
                <li><a href="solicitacao">Solicitacao</a></li>
                <li><a href="cotacao">Cotação</a></li>
                <li><a href="ordemcompra">Ordem de Compra</a></li>
            </ul>
        </li>

    </ul>
</li>
            
                            <li class="submenu">
    <a href="#">
        <svg class="icon" viewBox="0 0 98 107" fill="none" xmlns="http://www.w3.org/2000/svg">
            <path
                d="M68.0147 45.8274V23.0124C68.0147 17.97 66.0116 13.1341 62.4461 9.56862C58.8805 6.00309 54.0446 4 49.0022 4C43.9598 4 39.1239 6.00309 35.5584 9.56862C31.9929 13.1341 29.9898 17.97 29.9898 23.0124V45.8274M87.5645 35.7229L93.9679 96.5627C94.3228 99.9343 91.6864 102.865 88.2946 102.865H9.70985C8.90984 102.866 8.1186 102.698 7.38753 102.373C6.65646 102.048 6.0019 101.573 5.46639 100.979C4.93087 100.385 4.52636 99.6844 4.27915 98.9235C4.03194 98.1627 3.94755 97.3583 4.03146 96.5627L10.4399 35.7229C10.5877 34.3213 11.2492 33.0242 12.2968 32.0814C13.3444 31.1387 14.7039 30.6172 16.1132 30.6174H81.8912C84.8115 30.6174 87.2603 32.8229 87.5645 35.7229ZM31.891 45.8274C31.891 46.3316 31.6907 46.8152 31.3342 47.1718C30.9776 47.5283 30.494 47.7286 29.9898 47.7286C29.4855 47.7286 29.002 47.5283 28.6454 47.1718C28.2889 46.8152 28.0885 46.3316 28.0885 45.8274C28.0885 45.3231 28.2889 44.8395 28.6454 44.483C29.002 44.1264 29.4855 43.9261 29.9898 43.9261C30.494 43.9261 30.9776 44.1264 31.3342 44.483C31.6907 44.8395 31.891 45.3231 31.891 45.8274ZM69.9159 45.8274C69.9159 46.3316 69.7156 46.8152 69.3591 47.1718C69.0025 47.5283 68.5189 47.7286 68.0147 47.7286C67.5104 47.7286 67.0268 47.5283 66.6703 47.1718C66.3137 46.8152 66.1134 46.3316 66.1134 45.8274C66.1134 45.3231 66.3137 44.8395 66.6703 44.483C67.0268 44.1264 67.5104 43.9261 68.0147 43.9261C68.5189 43.9261 69.0025 44.1264 69.3591 44.483C69.7156 44.8395 69.9159 45.3231 69.9159 45.8274Z"
                stroke="white" stroke-width="8" stroke-linecap="round" stroke-linejoin="round"></path>
        </svg>
        <span>Produção</span>
    </a>
    <ul>

        <li><a href="processoprodutivo">Processo Produtivo</a></li>
        <li><a href="etapaproducao">Etapa de Produção</a></li>
        <li><a href="produtocomposicao">Engenharia do Produto</a></li>
        <li><a href="ordemproducao">Ordem de Produção</a></li>

    </ul>
</li>
            
                            <li class="submenu">
                <a href="#">
                    <svg class="icon" viewBox="0 0 20 19" fill="none" xmlns="http://www.w3.org/2000/svg">
                        <path
                            d="M11.5 14.875H14.875M14.875 14.875H18.25M14.875 14.875V11.5M14.875 14.875V18.25M4 8.5H6.25C6.84674 8.5 7.41903 8.26295 7.84099 7.84099C8.26295 7.41903 8.5 6.84674 8.5 6.25V4C8.5 3.40326 8.26295 2.83097 7.84099 2.40901C7.41903 1.98705 6.84674 1.75 6.25 1.75H4C3.40326 1.75 2.83097 1.98705 2.40901 2.40901C1.98705 2.83097 1.75 3.40326 1.75 4V6.25C1.75 6.84674 1.98705 7.41903 2.40901 7.84099C2.83097 8.26295 3.40326 8.5 4 8.5ZM4 18.25H6.25C6.84674 18.25 7.41903 18.0129 7.84099 17.591C8.26295 17.169 8.5 16.5967 8.5 16V13.75C8.5 13.1533 8.26295 12.581 7.84099 12.159C7.41903 11.7371 6.84674 11.5 6.25 11.5H4C3.40326 11.5 2.83097 11.7371 2.40901 12.159C1.98705 12.581 1.75 13.1533 1.75 13.75V16C1.75 16.5967 1.98705 17.169 2.40901 17.591C2.83097 18.0129 3.40326 18.25 4 18.25ZM13.75 8.5H16C16.5967 8.5 17.169 8.26295 17.591 7.84099C18.0129 7.41903 18.25 6.84674 18.25 6.25V4C18.25 3.40326 18.0129 2.83097 17.591 2.40901C17.169 1.98705 16.5967 1.75 16 1.75H13.75C13.1533 1.75 12.581 1.98705 12.159 2.40901C11.7371 2.83097 11.5 3.40326 11.5 4V6.25C11.5 6.84674 11.7371 7.41903 12.159 7.84099C12.581 8.26295 13.1533 8.5 13.75 8.5Z"
                            stroke="#341008" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                    </svg>
                    <span>Financeiro</span>
                </a>
                <ul>
                    <li class="subcat">
                        <a href="">Plano de Conta</a>
                        <ul>
                            <li><a href="planoconta">Plano de Conta</a></li>
                        </ul>
                    </li>

                    <li class="subcat">
                        <a href="">Centro de Custo</a>
                        <ul>
                            <li><a href="centrocusto">Centro de Custo</a></li>
                        </ul>
                    </li>

                    <li class="subcat">
                        <a href="">Despesas Fixas</a>
                        <ul>
                            <li><a href="despesafixa">Despesas Fixas</a></li>
                        </ul>
                    </li>


                    <li class="subcat">
                        <a href="">Contas a Receber</a>
                        <ul>
                            <li><a href="contareceber">Contas a Receber</a></li>
                            <li><a href="recebimento">Recebimento</a></li>
                        </ul>
                    </li>

                    <li class="subcat">
                        <a href="">Contas a Pagar</a>
                        <ul>
                            <li><a href="contapagar">Contas a Pagar</a></li>
                            <li><a href="pagamento">Pagamentos</a></li>
                        </ul>
                    </li>

                </ul>
            </li>            
            
            
                    </ul>
    </nav>

</div>
```

## 4 - Home 
Para configurar o arquivo home, façamos o seguinte procedimento:

- Crie um arquivo chamado home.blade.php dentro da pasta resources/views:
- no arquivo template recorte o conteúdo que você considera fazer parte do home do projeto
- Abra o arquivo home.blade.php, crie a marcação

```
@extends('template')
@section('conteudo')
//cole aqui o conteúdo do arquivo
@endsection
```

e cole o conteúdo copiado
- No arquivo index no local onde estava o conteúdo que foi recortado para o home faça um include ao arquivo home:

```
@extends('template')
@section('conteudo')
  <div class="home Venda">
        <div class="rows">
            <div class="col-12 mb-4 d-flex justify-between">
                <h1>Dashboard - ERP Mjailton</h1>
            </div>
            <div class="col-12">
                <div class="rows contas">
                    <div class="col-6 mb-4 d-flex">
                        <div class="caixa-home conta-receber hoje w-100">
                            <svg width="50" viewBox="0 0 75 69" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M48.4251 60.2399C51.5307 61.1343 54.7486 61.5866 57.9824 61.5833C63.1831 61.5907 68.3162 60.4146 72.9866 58.1455C73.1246 54.9089 72.1951 51.7158 70.3388 49.0503C68.4826 46.3848 65.8008 44.3921 62.7 43.3743C59.5991 42.3565 56.2482 42.369 53.1552 43.41C50.0622 44.451 47.3956 46.4637 45.5597 49.143M48.4251 60.2399V60.2291C48.4251 56.2099 47.3838 52.4291 45.5597 49.143M48.4251 60.2399V60.6227C41.4181 64.8083 33.3904 67.0136 25.2107 66.9999C16.7238 66.9999 8.78299 64.6708 2.00364 60.6227L2 60.2291C1.99721 55.1175 3.70982 50.1503 6.86782 46.1106C10.0258 42.071 14.4496 39.1887 19.4417 37.9182C24.4338 36.6477 29.7102 37.0613 34.4392 39.0936C39.1681 41.126 43.0806 44.6616 45.5597 49.143M37.5024 14.1875C37.5024 17.4198 36.2078 20.5197 33.9033 22.8053C31.5989 25.0909 28.4733 26.375 25.2144 26.375C21.9554 26.375 18.8299 25.0909 16.5254 22.8053C14.221 20.5197 12.9263 17.4198 12.9263 14.1875C12.9263 10.9552 14.221 7.85523 16.5254 5.56963C18.8299 3.28404 21.9554 2 25.2144 2C28.4733 2 31.5989 3.28404 33.9033 5.56963C36.2078 7.85523 37.5024 10.9552 37.5024 14.1875ZM67.5398 22.3125C67.5398 24.8265 66.5329 27.2376 64.7405 29.0153C62.9482 30.7929 60.5172 31.7916 57.9824 31.7916C55.4477 31.7916 53.0167 30.7929 51.2244 29.0153C49.432 27.2376 48.4251 24.8265 48.4251 22.3125C48.4251 19.7985 49.432 17.3874 51.2244 15.6097C53.0167 13.832 55.4477 12.8333 57.9824 12.8333C60.5172 12.8333 62.9482 13.832 64.7405 15.6097C66.5329 17.3874 67.5398 19.7985 67.5398 22.3125Z"
                                    stroke="white" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round" />
                            </svg>

                            <div>
                                <small><b>Clientes </b></small>
                                <h1>100</h1>
                            </div>
                        </div>
                    </div>
                    <div class="col-6 mb-4 d-flex">
                        <div class="caixa-home conta-receber hoje w-100">
                            <svg width="50" viewBox="0 0 64 70" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M45.1395 30.1875V14.8125C45.1395 11.4144 43.7896 8.1555 41.3868 5.75269C38.984 3.34988 35.7251 2 32.327 2C28.9289 2 25.67 3.34988 23.2672 5.75269C20.8644 8.1555 19.5145 11.4144 19.5145 14.8125V30.1875M58.3142 23.3781L62.6294 64.3781C62.8686 66.6502 61.0919 68.625 58.8062 68.625H5.84787C5.30875 68.6256 4.77553 68.5127 4.28286 68.2938C3.79019 68.0749 3.34908 67.7548 2.9882 67.3542C2.62731 66.9537 2.35472 66.4818 2.18812 65.969C2.02153 65.4563 1.96465 64.9142 2.0212 64.3781L6.33987 23.3781C6.43949 22.4336 6.88526 21.5594 7.59123 20.9241C8.2972 20.2888 9.21338 19.9373 10.1631 19.9375H54.4909C56.4589 19.9375 58.1092 21.4238 58.3142 23.3781ZM20.7958 30.1875C20.7958 30.5273 20.6608 30.8532 20.4205 31.0935C20.1802 31.3338 19.8543 31.4688 19.5145 31.4688C19.1747 31.4688 18.8488 31.3338 18.6086 31.0935C18.3683 30.8532 18.2333 30.5273 18.2333 30.1875C18.2333 29.8477 18.3683 29.5218 18.6086 29.2815C18.8488 29.0412 19.1747 28.9063 19.5145 28.9063C19.8543 28.9063 20.1802 29.0412 20.4205 29.2815C20.6608 29.5218 20.7958 29.8477 20.7958 30.1875ZM46.4208 30.1875C46.4208 30.5273 46.2858 30.8532 46.0455 31.0935C45.8052 31.3338 45.4793 31.4688 45.1395 31.4688C44.7997 31.4688 44.4738 31.3338 44.2336 31.0935C43.9933 30.8532 43.8583 30.5273 43.8583 30.1875C43.8583 29.8477 43.9933 29.5218 44.2336 29.2815C44.4738 29.0412 44.7997 28.9063 45.1395 28.9063C45.4793 28.9063 45.8052 29.0412 46.0455 29.2815C46.2858 29.5218 46.4208 29.8477 46.4208 30.1875Z"
                                    stroke="white" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round" />
                            </svg>

                            <div>
                                <small><b>Qtde de Vendas do Mês</b></small>
                                <h1>1000</h1>
                            </div>
                        </div>
                    </div>
                    <div class="col mb-4 d-flex">
                        <div class="caixa-home conta-receber hoje w-100">
                            <svg width="50" viewBox="0 0 66 76" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M45.1395 30.1875V14.8125C45.1395 11.4144 43.7897 8.1555 41.3868 5.75269C38.984 3.34988 35.7251 2 32.327 2C28.9289 2 25.67 3.34988 23.2672 5.75269C20.8644 8.1555 19.5145 11.4144 19.5145 14.8125V30.1875M59.5 38L58.3142 23.3781C58.1092 21.4238 56.4589 19.9375 54.4909 19.9375H10.1631C9.21338 19.9373 8.2972 20.2888 7.59123 20.9241C6.88525 21.5594 6.43949 22.4336 6.33987 23.3781L2.0212 64.3781C1.96465 64.9142 2.02153 65.4563 2.18812 65.969C2.35472 66.4818 2.62731 66.9537 2.9882 67.3542C3.34908 67.7548 3.79019 68.0749 4.28286 68.2938C4.77553 68.5127 5.30875 68.6256 5.84787 68.625H25.5M20.7958 30.1875C20.7958 30.5273 20.6608 30.8532 20.4205 31.0935C20.1802 31.3338 19.8543 31.4688 19.5145 31.4688C19.1747 31.4688 18.8488 31.3338 18.6086 31.0935C18.3683 30.8532 18.2333 30.5273 18.2333 30.1875C18.2333 29.8477 18.3683 29.5218 18.6086 29.2815C18.8488 29.0412 19.1747 28.9062 19.5145 28.9062C19.8543 28.9062 20.1802 29.0412 20.4205 29.2815C20.6608 29.5218 20.7958 29.8477 20.7958 30.1875ZM46.4208 30.1875C46.4208 30.5273 46.2858 30.8532 46.0455 31.0935C45.8052 31.3338 45.4793 31.4688 45.1395 31.4688C44.7997 31.4688 44.4738 31.3338 44.2336 31.0935C43.9933 30.8532 43.8583 30.5273 43.8583 30.1875C43.8583 29.8477 43.9933 29.5218 44.2336 29.2815C44.4738 29.0412 44.7997 28.9062 45.1395 28.9062C45.4793 28.9062 45.8052 29.0412 46.0455 29.2815C46.2858 29.5218 46.4208 29.8477 46.4208 30.1875Z"
                                    stroke="white" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round" />
                                <path
                                    d="M46.5 44.8333V68.1667M40.6667 62.6872L42.3758 63.9686C44.6528 65.6778 48.3453 65.6778 50.6242 63.9686C52.9031 62.2594 52.9031 59.4906 50.6242 57.7814C49.4867 56.9258 47.9933 56.5 46.5 56.5C45.0903 56.5 43.6806 56.0722 42.6053 55.2186C40.4547 53.5094 40.4547 50.7406 42.6053 49.0314C44.7558 47.3222 48.2442 47.3222 50.3947 49.0314L51.2017 49.6731M64 56.5C64 58.7981 63.5474 61.0738 62.6679 63.197C61.7884 65.3202 60.4994 67.2493 58.8744 68.8744C57.2493 70.4994 55.3202 71.7884 53.197 72.6679C51.0738 73.5474 48.7981 74 46.5 74C44.2019 74 41.9262 73.5474 39.803 72.6679C37.6798 71.7884 35.7507 70.4994 34.1256 68.8744C32.5006 67.2493 31.2116 65.3202 30.3321 63.197C29.4527 61.0738 29 58.7981 29 56.5C29 51.8587 30.8437 47.4075 34.1256 44.1256C37.4075 40.8437 41.8587 39 46.5 39C51.1413 39 55.5925 40.8437 58.8744 44.1256C62.1563 47.4075 64 51.8587 64 56.5Z"
                                    stroke="white" stroke-width="4.5" stroke-linecap="round" stroke-linejoin="round" />
                            </svg>
                            <div>
                                <small><b>Total de Vendas do mês</b></small>
                                <h1>R$ 100</h1>
                            </div>
                        </div>
                    </div>
                    <div class="col mb-4 d-flex">
                        <div class="caixa-home conta-receber hoje w-100">
                            <svg width="50" viewBox="0 0 35 28" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M21 5.84999L24.299 2.54925C24.6507 2.19757 25.1277 2 25.625 2C26.1223 2 26.5993 2.19757 26.951 2.54925C27.3027 2.90092 27.5002 3.3779 27.5002 3.87525C27.5002 4.37259 27.3027 4.84957 26.951 5.20125L12.582 19.5702C12.0533 20.0986 11.4014 20.487 10.685 20.7002L8 21.5002L8.8 18.8152C9.01328 18.0989 9.40163 17.4469 9.93 16.9182L22.613 4.23725L21 5.84999ZM21 5.84999L22.613 7.5"
                                    stroke="white" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" />
                                <rect y="25" width="35" height="3" rx="1.5" fill="white" />
                            </svg>
                            <div>
                                <small><b>Orçamentos abertos</b></small>
                                <h1>10</h1>
                            </div>
                        </div>
                    </div>
                    <div class="col mb-4 d-flex">
                        <div class="caixa-home conta-receber hoje w-100">
                            <svg width="70" viewBox="0 0 41 30" fill="none" xmlns="http://www.w3.org/2000/svg">
                                <path
                                    d="M23.79 21.6667L26.5 25L32 17M33 23C33 23.7879 32.8448 24.5681 32.5433 25.2961C32.2417 26.0241 31.7998 26.6855 31.2426 27.2426C30.6855 27.7998 30.0241 28.2417 29.2961 28.5433C28.5681 28.8448 27.7879 29 27 29C26.2121 29 25.4319 28.8448 24.7039 28.5433C23.9759 28.2417 23.3145 27.7998 22.7574 27.2426C22.2002 26.6855 21.7583 26.0241 21.4567 25.2961C21.1552 24.5681 21 23.7879 21 23C21 21.4087 21.6321 19.8826 22.7574 18.7574C23.8826 17.6321 25.4087 17 27 17C28.5913 17 30.1174 17.6321 31.2426 18.7574C32.3679 19.8826 33 21.4087 33 23Z"
                                    stroke="white" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" />
                                <path
                                    d="M21 5.84999L24.299 2.54925C24.6507 2.19757 25.1277 2 25.625 2C26.1223 2 26.5993 2.19757 26.951 2.54925C27.3027 2.90092 27.5002 3.3779 27.5002 3.87525C27.5002 4.37259 27.3027 4.84957 26.951 5.20125L12.582 19.5702C12.0533 20.0986 11.4014 20.487 10.685 20.7002L8 21.5002L8.8 18.8152C9.01328 18.0989 9.40163 17.4469 9.93 16.9182L22.613 4.23725L21 5.84999ZM21 5.84999L22.613 7.5"
                                    stroke="white" stroke-width="2.5" stroke-linecap="round" stroke-linejoin="round" />
                                <rect y="25" width="17" height="3" rx="1.5" fill="white" />
                                <rect x="36" y="25" width="5" height="3" rx="1.5" fill="white" />
                            </svg>

                            <div>
                                <small><b>Orçamentos Concretizados</b></small>
                                <h1>10</h1>
                            </div>
                        </div>
                    </div>
                </div>
            </div>


            <div class="col-12 mt-4">

                <div class="rows contas">
                    <div class="col-6 mb-4">
                        <div class="tabela-responsiva">
                            <span class="h5 text-uppercase center-middle d-flex">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="icon">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M8.25 6.75h12M8.25 12h12m-12 5.25h12M3.75 6.75h.007v.008H3.75V6.75zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zM3.75 12h.007v.008H3.75V12zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm-.375 5.25h.007v.008H3.75v-.008zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z" />
                                </svg>
                                Últimas Vendas</span>
                            <div class="p-0 d-block home tscroll2">
                                <table class="table" cellpadding="0" cellspacing="0">
                                    <thead>
                                        <tr>
                                            <th>id</th>
                                            <th align="left">Vendas</th>
                                            <th>Data</th>
                                            <th>Ver</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>1</td>
                                            <td>Vendas</td>
                                            <td class="text-center">29/07/2023</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>1</td>
                                            <td>Vendas</td>
                                            <td class="text-center">29/07/2023</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>1</td>
                                            <td>Vendas</td>
                                            <td class="text-center">29/07/2023</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>1</td>
                                            <td>compra</td>
                                            <td class="text-center">29/07/2023</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                    <div class="col-6 mb-4">
                        <div class="tabela-responsiva">
                            <span class="h5 text-uppercase center-middle d-flex">
                                <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24"
                                    stroke-width="1.5" stroke="currentColor" class="icon">
                                    <path stroke-linecap="round" stroke-linejoin="round"
                                        d="M8.25 6.75h12M8.25 12h12m-12 5.25h12M3.75 6.75h.007v.008H3.75V6.75zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zM3.75 12h.007v.008H3.75V12zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0zm-.375 5.25h.007v.008H3.75v-.008zm.375 0a.375.375 0 11-.75 0 .375.375 0 01.75 0z" />
                                </svg>

                                Clientes com Débitos </span>
                            <div class="p-0 d-block home tscroll2">
                                <table class="table" cellpadding="0" cellspacing="0">
                                    <thead>
                                        <tr>
                                            <th>id</th>
                                            <th align="left">Cliente</th>
                                            <th class="text-center">Débito</th>
                                            <th>Ver</th>
                                        </tr>
                                    </thead>
                                    <tbody>
                                        <tr>
                                            <td>1</td>
                                            <td>Cliente</td>
                                            <td class="text-center">R$100,00</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>1</td>
                                            <td>Cliente </td>
                                            <td class="text-center">R$100,00</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>1</td>
                                            <td>Cliente </td>
                                            <td class="text-center">R$100,00</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                        <tr>
                                            <td>1</td>
                                            <td>Cliente </td>
                                            <td class="text-center">R$100,00</td>
                                            <td class="text-center"><a href="" class="fas fa-eye text-verde"></a>
                                            </td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
@endsection
```

## 5 - Template
O arquivo template representa a estrutura fixa do sistema que envolverá todas as views, teoricamente seria o conteúdo do arquivo index, excluindo a parte que foi tirada para o cabeçalho, o menu e home.

no template também iremos configurar os recursos principais do projeto como o css e o javascript e outras bibliotecas necessárias.

Para tornar o layout dinâmico, precisamos ajustar o include do home da seguinte forma:

Ao invés de incluir o arquivo diretamente pelo include iremos chamar o método @yield passar como parâmetro a palavra 'conteudo',
ficando: @yield('conteudo')

Modifique o arquivo template implementando o código acima.

```
<!DOCTYPE html>
<html lang="pt-br">

<head>
    <title>Sistema Comercial - mjailton</title>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale =1">
    <!--css-->
    <link rel="stylesheet" href="{{ asset('assets/componentes/css/style_Componente.css') }}">
    <link rel="stylesheet" href="{{ asset('assets/js/datatables/css/jquery.dataTables.min.css') }}">
    <link rel="stylesheet" href="{{ asset('assets/js/datatables/css/responsive.dataTables.min.css') }}">

    <link rel="stylesheet" href="{{ asset('assets/css/auxiliar.css') }}">
    <link rel="stylesheet" href="{{ asset('assets/css/grade.css') }}">
    <link rel="stylesheet" href="{{ asset('assets/css/style.css') }}">
    <link rel="stylesheet" href="{{ asset('assets/css/home-venda.css') }}">
    <link rel="stylesheet" href="{{ asset('assets/css/style-m.css') }}">
    <!--font icones-->
    <link rel="stylesheet" href="https://use.fontawesome.com/releases/v5.6.3/css/all.css"
        integrity="sha384-UHRtZLI+pbxtHCWp1t77Bi1L4ZtiqrqD80Kn4Z8NTSRyMA2Fd33n5dQ8lWUE00s/" crossorigin="anonymous">

    <script src="{{ asset('assets/js/jquery.min.js') }}"></script>
    <script src="https://code.jquery.com/ui/1.12.1/jquery-ui.js"></script>

    <script>
        var base_url = "{{ asset('') }}";
        var _token = "{{ csrf_token() }}";
    </script>
</head>

<body>
    @include('cabecalho')
    @include('menu')
    @include('inc.erros')
    @include('inc.msg')
    <div id="mostrarErros"></div>
    <div id="mostrarUmErro"></div>
    <div id="mostrarSucesso"></div>

    <div class="conteudo">
        @yield('conteudo')
    </div>


    <script src="{{ asset('assets/js/datatables/js/dataTables.responsive.min.js') }}"></script>
    <script src="{{ asset('assets/js/datatables/js/jquery.dataTables.min.js') }}"></script>

    <script src="{{ asset('assets/js/jquery.mask.js') }}"></script>

    <script src="{{ asset('assets/componentes/js/js_data_table.js') }}"></script>
    <script src="{{ asset('assets/componentes/js/js_modal.js') }}"></script>
    <script src="{{ asset('assets/componentes/js/js_util.js') }}"></script>
    <script src="{{ asset('assets/componentes/js/js_mascara.js') }}"></script>
    <script src="{{ asset('assets/componentes/js/upload.js') }}"></script>

</body>

</html>
```

## 6 - Rodando o projeto
Ajuste seu projeto de forma que consiga renderizar todas as imagens, css, javascript e em seguida execute.

# TABELA STATUS - CONFIGURANDO MODEL
Configurando Model Status. 

<a href="https://mjailton.com.br/campus/conteudo/passo/1481/38173/662/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula**</a>

## 1 - model Status
Crie o model status

```
php artisan make:model Status -m
```

## 2 - migration statuses
adicione os seguintes campos:
- status varchar(80)
- descricao text

em seguida renomeie a migration statuses para que a mesma seja a primeira a aparecer na lista

```
Schema::create('statuses', function (Blueprint $table) {
            $table->id();
            $table->string('status',80);
            $table->text('descricao');
            $table->timestamps();
        });
```

## 3 - fillable status
Configure os fillables do Model Status

```
protected $fillable=["id","status", "descricao" ];
```

## 4 - StatusSeeder
Crie a seed Status. Para criar a seed status use o comando:

```
php artisan make:seed StatusSeeder
```
## 5 - Model User
Vamos fazer algumas alterações no model user

### migration Users
Modifique a migration users acrescentando os campos,

- eh_admin varchar(1)
- status_id integer

```
Schema::create('users', function (Blueprint $table) {
            $table->id();
            $table->string('name');
            $table->string('email')->unique();
            $table->timestamp('email_verified_at')->nullable();
            $table->string('password');
            $table->string('eh_admin',1)->defaul('N');
            $table->integer('status_id')->nullable();
            $table->rememberToken();
            $table->timestamps();
        });
```

### fillable User
Configure os fillables do Model User

```
protected $fillable = [
        'name',
        'email',
        'password',
        'status_id',
        'eh_admin'
    ];
```

### Próximo passo

```
php artisan migrate:fresh --seed
```

# TABELA STATUS - MOSTANDO DADOS
Listagem.

<a href="https://mjailton.com.br/campus/conteudo/passo/1481/38178/663/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula**</a> 

## 1 - Criando o Controller
Crie um controller de recursos chamado Status, para que o projeto fique mais organizado salve o controller numa pasta chamada Cadastro

### Comando de Criação
Para criar o controller use o comando:

```
php artisan make:controller \Cadastro\StatusController -r
```

### Método Index
No controller StatusController implemente o método index, o qual deverá:

- pegar a lista de status e colocar um array
- chamar a view Status/Index com o array criado com a lista de categorias

```
public function index()
    {
        $dados["lista"] = Status::get();
        return View("Cadastro.Status.Index", $dados);
    }
```
**Obs:** Não esqueça de ver no topo do código se importou **use App\Models\Status;****


## 2 - Criando a Rota
Crie uma rota resource setando para o controller **StatusController**

```
Route::resource("/status", StatusController::class);
```

### Chamando a Rota
Localize no menu o local para chamar a rota status.index

```
<li><a href="{{ route('status.index') }}">Status</a></li>
```

## 3 - Criando a View
Crie a view para a listagem de status

### Criando a View
Dentro da pasta resources/view crie uma pasta chamada de Cadastro e dentro de Cadastro crie uma outra chamada de Status e dentro da pasta Status crie um arquivo chamado Index.blade.php

### Montando o conteudo

Copie o conteúdo do arquivo lst_status para o arquivo Cadastro/Status/Index.blade.php, não esqueça envolvê-lo pelos comandos:

```
@extends('template')
@section('conteudo')

//aqui fica o conteúdo do arquivo

@endsection
```

### Testando o Sistema
Execute seu sistema e pelo menu categoria abre a página de listagem de categoria, mas deverá está parecida com imagem abaixo

## 4 - Listando dados do banco
Na view Index, faça os seguintes procedimentos:

- Faça o loop para receber os dados do banco e listar na tabela
- Não crie nenhum link para fazer a edição
- Não crie nenhum link para fazer a exclusão de um registro

**Exemplo:**
```
@foreach ($lista as $l)
                                <tr>
                                    <td align="center">{{ $l->id }}</td>
                                    <td align="left">{{ $l->categoria }}</td>
                                    <td align="center">
                                        <a href="{{ route('categoria.edit', $l->id) }}"
                                            class="d-inline-block btn btn-outline-roxo btn-pequeno"><i
                                                class="fas fa-edit"></i>
                                            Editar</a>

                                        <a href="javascript:;"
                                            onclick="confirm('Tem Certeza?') ? document.getElementById('apagar{{ $l->id }}').submit() : '';"
                                            class="d-inline-flex gap-3 btn btn-outline-vermelho btn-pequeno">
                                            <i class="fas fa-trash-alt"></i>
                                            <form action="{{ route('categoria.destroy', $l->id) }}" method="POST"
                                                id="apagar{{ $l->id }}">
                                                @method('DELETE')
                                                @csrf
                                            </form>

                                            Excluir
                                        </a>
                                    </td>
                                </tr>
                            @endforeach
```

# TABELA CATEGORIA - CONFIGURANDO MODEL

<a href="https://mjailton.com.br/campus/conteudo/passo/1482/38188/664/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula**</a>

<a href="https://mjailton.com.br/campus/objetivo/completo/209" target="_blank">**Linha do Tempo**</a>


## 1 - model Categoria
Crie o model categoria

### Comando de Criação
Para criar o model status use o comando:
 
```
php artisan make:model Categoria -m
```

## 2 - migration categorias
adicione os seguintes campos:
adicione o campo categoria varchar(80)

```
Schema::create('categorias', function (Blueprint $table) {
            $table->id();
            $table->string("categoria", 80);
            $table->timestamps();
        });
		
```		

## 3 - fillable Categoria
Configure os fillables do Model Categoria

```
protected $fillable=["id", "categoria"];
```

## 4 - CategoriaSeeder
Crie a seed Categoria

```
Categoria ::firstOrCreate([
            'categoria' => 'Panela'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Cuzcuzeira'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Copo'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Panela'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Caneca'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Papeiro'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Leiteira'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Frigideira'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Bacia'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Balde'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Assadeira'
        ]);

        Categoria::firstOrCreate([
            'categoria' => 'Baquelite'
        ]);
		
```

# TABELA CATEGORIA - LISTANDO DADOS

<a href="https://mjailton.com.br/campus/conteudo/passo/1476/38193/665/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula**</a> 


## 1 - Criando o Controller
Crie um controller de recursos chamado **Categoria**, para que o projeto fique mais organizado salve o controller numa pasta chamada Cadastro

Para criar o controller use o comando: 
```
php artisan make:controller \Cadastro\CategoriaController -r
```

## 2 - Criando a Rota
Crie uma rota resource setando para o controller CategoriaController

```
Route::resource("/categoria", CategoriaController::class);
```
### Chamando a Rota

```
 <li><a href="{{ route('categoria.index') }}">Categoria</a></li>
```

## 3 - Criando a View
Crie a view para a listagem de categoria

### Criando a View
Dentro da pasta **resources/view** crie uma pasta chamada de Cadastro e dentro de Cadastro crie uma outra chamada de **Categoria** e dentro da pasta Categoria crie um arquivo chamado **Index.blade.php**.

### Montando o conteudo
Copie o conteúdo do arquivo **lst_categoria** para o arquivo **Cadastro/Categoria/Index.blade.php**, não esqueça envolvê-lo pelos comandos:

```
@extends('template')
@section('conteudo')

//aqui fica o conteúdo do arquivo

@endsection
```

### Testando o Sistema
Execute seu sistema e pelo menu categoria abre a página de listagem de categoria.

### Listando dados do banco
Na view Index, faça os seguintes procedimentos:

- Faça o loop para receber os dados do banco e listar na tabela
- Configure o link para fazer a edição de um registro
- Configure o link para fazer a exclusão de um registro

```
 @foreach ($lista as $l)
                                <tr>
                                    <td align="center">{{ $l->id }}</td>
                                    <td align="left">{{ $l->categoria }}</td>
                                    <td align="center">
                                        <a href="{{ route('categoria.edit', $l->id) }}"
                                            class="d-inline-block btn btn-outline-roxo btn-pequeno"><i
                                                class="fas fa-edit"></i>
                                            Editar</a>

                                        <a href="javascript:;"
                                            onclick="confirm('Tem Certeza?') ? document.getElementById('apagar{{ $l->id }}').submit() : '';"
                                            class="d-inline-flex gap-3 btn btn-outline-vermelho btn-pequeno">
                                            <i class="fas fa-trash-alt"></i>
                                            <form action="{{ route('categoria.destroy', $l->id) }}" method="POST"
                                                id="apagar{{ $l->id }}">
                                                @method('DELETE')
                                                @csrf
                                            </form>

                                            Excluir
                                        </a>
                                    </td>
                                </tr>
                            @endforeach
```

#TABELA CATEGORIA - INSERINDO DADOS

<a href="https://mjailton.com.br/campus/conteudo/passo/1482/38198/666/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula**</a>


## 1 - Configurando Formulário
Abra o arquivo **Cadastro/Categoria/Index.blade.php** e Configure os dados do formulário para inserção dos dados

### Configurando o form
Configure o elemento form da view **Index**, com as seguintes ações:

- Setar a rota categoria.store na propriedade action do form
- Setar o método post na propriedade method do form
- implementar o helper **@csrf** dentro do form

```
<form action="{{ route('categoria.store') }}" method="POST">
  @csrf
```



## 2 - Método store
implemente o método store para receber e salvar os dados do formulário no Banco de dados

```
$req = $request->except(["_token"]);
        try {
            Categoria::Create($req);
            return redirect()->route("categoria.index")->with("msg_sucesso", "Registro Inserido com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
```

## 3 - Criando o request
Uma boa prática de programação é validar os dados antes de enviá-los para o banco de dados e uma bom recurso que o laravel oferece são os requests.
implemente um request de forma que faça todas as validações necessárias para salvar a informações no banco

###Comando de Criação

Para criar um request use os seguinte comando:
```
php artisan make:request CategoriaRequest
```

## 4 - CategoriaRequest
No método store troque o parâmetro Request para CategoriaRequest

```
public function store(CategoriaRequest $request)
    {
        $req = $request->except(["_token"]);
        try {
            Categoria::Create($req);
            return redirect()->route("categoria.index")->with("msg_sucesso", "Registro Inserido com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }

```


## 5 - Testando o sistema
Teste o sistema fazendo cadastros


#TABELA CATEGORIA - ALTERANDO DADOS

<a href="https://mjailton.com.br/campus/conteudo/passo/1482/38203/667/?f=2001" target="_blank">**Acesse aqui o Vídeo da Aula**</a>


## 1 - Metodo Edit
Configure o método **edit** do Controller, com as seguinte ações:

- Busque a categoria pelo id passado no parâmetro e guarde a informação em um array
- liste todas as categorias e guarde as informações em um array
- Chame a view **Index**, passando o array de dados como parâmetro

```
public function edit(string $id)
    {
        $dados["categoria"] = Categoria::find($id);
        $dados["lista"] = Categoria::get();
        return View('Cadastro.Categoria.Index', $dados);
    }

```

## 2 - Configurando Formulário
Configure os dados do formulário para ediççao dos dados

### Configurando o form
Configure o elemento form da view Index, com as seguintes ações:

- o sistema deve verificar se o objeto categoria existe,
- caso ele exista, no formulário deve ser configurada a rota categoria.update
- caso não exista, no formulário deve ser configurada a rota categoria.store

```
@if (isset($categoria))
                        <form action="{{ route('categoria.update', $categoria->id) }}" method="POST">
                            @method('put')
                        @else
                            <form action="{{ route('categoria.store') }}" method="POST">
                    @endif
```

### Configure os inputs
na propriedade value de cada input, faça uma verificação se existe o objeto categoria, se existir imprimir o valor do campo correspondente, senão existe imprimir o objeto old()

```
<div class="{{ isset($categoria->categoria) ? 'bg-edit' : 'caixafield' }}  p-2 radius-4 border">
                        <div class="   p-2 pt-0 radius-4">
                            <div class="rows center-middle">
                                <div class="col-9">
                                    <label class="text-label d-block text-branco">Nome </label>
                                    <input type="text" name="categoria"
                                        value="{{ $categoria->categoria ?? old('categoria') }}" class="form-campo">
                                </div>
                                <div class="col-3 mt-0 pt-4">
                                    <input type="submit" value="Salvar" class="w-100 btn btn-roxo text-uppercase">
                                </div>
                            </div>
                        </div>
                    </div>
```

### Método update
Implemente o método update de forma que o mesmo receba os dados do formulário e salve no banco de dados, caso ache necessário use um bloco try/catch

```
 $req = $request->except(["_token", "_method"]);
        try {
            Categoria::find($id)->update($req);
            return redirect()->route("categoria.index")->with("msg_sucesso", "Registro Alterado com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
```



## 3 - Testando o sistema
Faça o teste do seu sistema de forma que o mesmo consiga criar um novo registro e também alterá-lo

# TABELA-UNIDADE

## CONFIGURANDO-MODEL
Configurando Model Unidade, <a href="https://mjailton.com.br/campus/conteudo/passo/1483/38448/669/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

### 1 - model Unidade
Crie o model Unidade

Comando de Criação
```
php artisan make:model Unidade -m
```

### 2 - migration unidades
adicione os seguintes campos:

- abrev varchar(20)
- unidade varchar(60)

```
Schema::create('unidades', function (Blueprint $table) {
            $table->id();
            $table->string('abrev',20);
            $table->string('unidade',60);
            $table->timestamps();
        });
```

### 3 - fillable unidade
Configure os fillables do Model Unidade

```
protected $fillable=["id", "abrev", "unidade"];
```

### 4 - UnidadeSeeder
Crie a seed Unidade. Lembrando que não é obrigatório, a menos que queira já popular a tabela com dados.

Comando de Criação
```
php artisan make:seed UnidadeSeeder
```

Popular dados
```
public function run()
    {
        Unidade::firstOrCreate(['unidade'    => "UNID",  'abrev'  => "UNID"  ]);
        Unidade::firstOrCreate(['unidade'    => "AMPOLA", 'abrev'  => "AMPOLA"  ]);
        Unidade::firstOrCreate(['unidade'    => "BALDE", 'abrev'  => "BALDE"  ]);
        Unidade::firstOrCreate(['unidade'    => "BANDEJ", 'abrev'  => "BANDEJ"  ]);
        Unidade::firstOrCreate(['unidade'    => "BARRA", 'abrev'  => "BARRA"  ]);
        Unidade::firstOrCreate(['unidade'    => "BISNAG", 'abrev'  => "BISNAG"  ]);
        Unidade::firstOrCreate(['unidade'    => "BLOCO", 'abrev'  => "BLOCO"  ]);
        Unidade::firstOrCreate(['unidade'    => "BOBINA", 'abrev'  => "BOBINA"  ]);
        Unidade::firstOrCreate(['unidade'    => "BOMB", 'abrev'  => "BOMB"  ]);
        Unidade::firstOrCreate(['unidade'    => "CAPS", 'abrev'  => "CAPS"  ]);
        Unidade::firstOrCreate(['unidade'    => "CART", 'abrev'  => "CART"  ]);
        Unidade::firstOrCreate(['unidade'    => "CENTO", 'abrev'  => "CENTO"  ]);
        Unidade::firstOrCreate(['unidade'    => "CJ", 'abrev'  => "CJ"  ]);
        Unidade::firstOrCreate(['unidade'    => "CM", 'abrev'  => "CM"  ]);
        Unidade::firstOrCreate(['unidade'    => "CM2", 'abrev'  => "CM2"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX", 'abrev'  => "CX"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX2", 'abrev'  => "CX2"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX3", 'abrev'  => "CX3"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX5", 'abrev'  => "CX5"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX10", 'abrev'  => "CX10"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX15", 'abrev'  => "CX15"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX20", 'abrev'  => "CX20"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX25", 'abrev'  => "CX25"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX50", 'abrev'  => "CX50"  ]);
        Unidade::firstOrCreate(['unidade'    => "CX100", 'abrev'  => "CX100"  ]);
        Unidade::firstOrCreate(['unidade'    => "DISP", 'abrev'  => "DISP"  ]);
        Unidade::firstOrCreate(['unidade'    => "DUZIA", 'abrev'  => "DUZIA"  ]);
        Unidade::firstOrCreate(['unidade'    => "EMBAL", 'abrev'  => "EMBAL"  ]);
        Unidade::firstOrCreate(['unidade'    => "FARDO", 'abrev'  => "FARDO"  ]);
        Unidade::firstOrCreate(['unidade'    => "FOLHA", 'abrev'  => "FOLHA"  ]);
        Unidade::firstOrCreate(['unidade'    => "FRASCO", 'abrev'  => "FRASCO"  ]);
        Unidade::firstOrCreate(['unidade'    => "GALAO", 'abrev'  => "GALAO"  ]);
        Unidade::firstOrCreate(['unidade'    => "GF", 'abrev'  => "GF"  ]);
        Unidade::firstOrCreate(['unidade'    => "GRAMAS", 'abrev'  => "GRAMAS"  ]);
        Unidade::firstOrCreate(['unidade'    => "JOGO", 'abrev'  => "JOGO"  ]);
        Unidade::firstOrCreate(['unidade'    => "KG", 'abrev'  => "KG"  ]);
        Unidade::firstOrCreate(['unidade'    => "KIT", 'abrev'  => "KIT"  ]);
        Unidade::firstOrCreate(['unidade'    => "LATA", 'abrev'  => "LATA"  ]);
        Unidade::firstOrCreate(['unidade'    => "LITRO", 'abrev'  => "LITRO"  ]);
        Unidade::firstOrCreate(['unidade'    => "M", 'abrev'  => "M"  ]);
        Unidade::firstOrCreate(['unidade'    => "M2", 'abrev'  => "M2"  ]);
        Unidade::firstOrCreate(['unidade'    => "M3", 'abrev'  => "M3"  ]);
        Unidade::firstOrCreate(['unidade'    => "MILHEI", 'abrev'  => "MILHEI"  ]);
        Unidade::firstOrCreate(['unidade'    => "ML", 'abrev'  => "ML"  ]);
        Unidade::firstOrCreate(['unidade'    => "MWH", 'abrev'  => "MWH"  ]);
        Unidade::firstOrCreate(['unidade'    => "PACOTE", 'abrev'  => "PACOTE"  ]);
        Unidade::firstOrCreate(['unidade'    => "PALETE", 'abrev'  => "PALETE"  ]);
        Unidade::firstOrCreate(['unidade'    => "PARES", 'abrev'  => "PARES"  ]);
        Unidade::firstOrCreate(['unidade'    => "PC", 'abrev'  => "PC"  ]);
        Unidade::firstOrCreate(['unidade'    => "POTE", 'abrev'  => "POTE"  ]);
        Unidade::firstOrCreate(['unidade'    => "RESMA", 'abrev'  => "RESMA"  ]);
        Unidade::firstOrCreate(['unidade'    => "ROLO", 'abrev'  => "ROLO"  ]);
        Unidade::firstOrCreate(['unidade'    => "SACO", 'abrev'  => "SACO"  ]);
    }
```

### 5 Configurar a DatabaseSeeder comodando a unidade

Exemplo:
```
public function run(): void
    {
       $this->call([
           StatusSeeder::class,
           CategoriaSeeder::class,
           UnidadeSeeder::class,
       ]);
    }
```

# TABELA-UNIDADE-LISTANDO

<a href="https://mjailton.com.br/campus/conteudo/passo/1483/38454/670/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Criando o Controller
Crie um controller de recursos chamado Unidade, para que o projeto fique mais organizado salve o controller numa pasta chamada Cadastro

### Comando de Criação
Para criar o controller use o comando: 

```
php artisan make:controller \Cadastro\UnidadeController -r
```

### Método Index
No controller UnidadeController implemente o método index, o qual deverá:

- pegar a lista de categorias e colocar um array
- chamar a view Categoria/Index com o array criado com a lista de unidade

```
public function index()
    {
        $dados["lista"] = Unidade::get();
        return View("Cadastro.Unidade.Index", $dados);
    }
```

## 2 - Criando a Rota
Crie uma rota resource setando para o controller UnidadeController

```
Route::resource("/unidade", UnidadeController::class);
```
### Chamando a Rota

```
 <li><a href="{{ route('unidade.index') }}">Unidade</a></li>
 ```
 
## 3 - Criando a View
Crie a view para a listagem de unidade

### Criando a View
Dentro da pasta **resources/view** crie uma pasta chamada de **Cadastro** e dentro de Cadastro crie uma outra chamada de **Unidade** e dentro da pasta Unidade crie um arquivo chamado **Index.blade.php**

## 4 - Listando dados do banco
Na view Index, faça os seguintes procedimentos:

- Faça o loop para receber os dados do banco e listar na tabela
- Configure o link para fazer a edição de um registro
- Configure o link para fazer a exclusão de um registro

```
 @foreach ($lista as $l)
                                <tr>
                                    <td align="center">{{ $l->id }}</td>
                                    <td align="left">{{ $l->categoria }}</td>
                                    <td align="center">
                                        <a href="{{ route('categoria.edit', $l->id) }}"
                                            class="d-inline-block btn btn-outline-roxo btn-pequeno"><i
                                                class="fas fa-edit"></i>
                                            Editar</a>

                                        <a href="javascript:;"
                                            onclick="confirm('Tem Certeza?') ? document.getElementById('apagar{{ $l->id }}').submit() : '';"
                                            class="d-inline-flex gap-3 btn btn-outline-vermelho btn-pequeno">
                                            <i class="fas fa-trash-alt"></i>
                                            <form action="{{ route('categoria.destroy', $l->id) }}" method="POST"
                                                id="apagar{{ $l->id }}">
                                                @method('DELETE')
                                                @csrf
                                            </form>

                                            Excluir
                                        </a>
                                    </td>
                                </tr>
                            @endforeach
```


# TABELA-UNIDADE-INSERINDO

<a href="https://mjailton.com.br/campus/conteudo/passo/1483/38460/671/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Configurando Formulário
Configure os dados do formulário para inserção dos dados

### Configurando o form
Configure o elemento form da view Index, com as seguintes ações:

- Setar a rota unidade.store na propriedade action do form
- Setar o método post na propriedade method do form
- implementar o helper @csrf dentro do form

```
<form action="{{ route('unidade.store') }}" method="POST">
  @csrf
```

## 2 - Método store
implemente o método store para receber e salvar os dados do formulário no Banco de dados

```
public function store(Request $request)
    {
        $req = $request->except(["_token"]);
        try {
            Unidade::Create($req);
            return redirect()->route("unidade.index")->with("msg_sucesso", "Registro Inserido com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }
```

## 3 - Criando o request
Uma boa prática de programação é validar os dados antes de enviá-los para o banco de dados e uma bom recurso que o laravel oferece são os requests.
implemente um request de forma que faça todas as validações necessárias para salvar a informações no banco.

### Comando de Criação
Para criar um request use os seguinte comando:
```
php artisan make:request UnidadeRequest
```

## 4 - UnidadeRequest
No arquivo de request configure as validações necessárias e não esqueça de setar o método authorize para true;

```
public function rules()
    {
        $id= $this->segment(2);
        return [
            "unidade" => "required|unique:unidades,unidade,{$id},id",
            "abrev" => "required|unique:unidades,abrev,{$id},id"
        ];
    }
```

### Troque o parâmetro Request 
No método store troque o parâmetro Request para UnidadeRequest:

```
public function store(UnidadeRequest $request)
    {
        $req = $request->except(["_token"]);
        try {
            Unidade::Create($req);
            return redirect()->route("unidade.index")->with("msg_sucesso", "Registro Inserido com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }

```

## 5 - Testando o sistema
Teste o sistema fazendo cadastros


# TABELA-UNIDADE-ALTERANDO

<a href="https://mjailton.com.br/campus/conteudo/passo/1483/38466/672/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Metodo Edit
Configure o método edit do Controller, com as seguinte ações:

- Busque a unidade pelo id passado no parâmetro e guarde a informação em um array
- liste todas as unidades e guarde as informações em um array
- Chame a view Index, passando o array de dados como parâmetro

```
public function edit($id)
    {
        $dados["unidade"] = Unidade::find($id);
        $dados["lista"] = Unidade::get();
        return View('Cadastro.Unidade.Index', $dados);
    }
```

## 2 - Configurando Formulário
Configure os dados do formulário para ediççao dos dados

### Configurando o form
Configure o elemento form da view Index, com as seguintes ações:

- o sistema deve verificar se o objeto unidade existe,
- caso ele exista, no formulário deve ser configurada a rota unidade.update
- caso não exista, no formulário deve ser configurada a rota unidade.store

```
@if (isset($unidade))
                        <form action="{{ route('unidade.update', $unidade->id) }}" method="POST">
                            @method('put')
                        @else
                            <form action="{{ route('unidade.store') }}" method="POST">
                    @endif
```

### Configure os inputs
na propriedade value de cada input, faça uma verificação se existe o objeto unidade, se existir imprimir o valor do campo correspondente, senão existe imprimir o objeto old()

```
        <div class="{{ isset($unidade->unidade) ? 'bg-edit' : 'caixafield' }}  p-2 radius-4 border">
                        <div class="   p-2 pt-0 radius-4">
                            <div class="rows center-middle">
                                <div class="col-6">
                                    <label class="text-label d-block text-branco">Nome </label>
                                    <input type="text" name="unidade" value="{{ $unidade->unidade ?? old('unidade') }}"
                                           class="form-campo">
                                </div>
                                <div class="col-3">
                                    <label class="text-label d-block text-branco">Abrev </label>
                                    <input type="text" name="abrev" value="{{ $unidade->abrev ?? old('abrev') }}"
                                           class="form-campo">
                                </div>
                                <div class="col-3 mt-0 pt-4">
                                    <input type="submit" value="Salvar" class="w-100 btn btn-roxo text-uppercase">
                                </div>
                            </div>
                        </div>
                    </div>
```

### Método update
Implemente o método update de forma que o mesmo receba os dados do formulário e salve no banco de dados, caso ache necessário use um bloco try/catch

```
public function update(UnidadeRequest $request, string $id)
    {
        $req = $request->except(["_token", "_method"]);
        try {
            Unidade::find($id)->update($req);
            return redirect()->route("unidade.index")->with("msg_sucesso", "Registro Alterado com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }
```


## 3 - Testando o sistema
Faça o teste do seu sistema de forma que o mesmo consiga criar um novo registro e também alterá-lo


# TABELA-UNIDADE-EXCLUINDO

<a href="https://mjailton.com.br/campus/conteudo/passo/1483/38472/673/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Método destroy
implemente o método destroy do Controller, com as seguinte ações:

- Busque a unidade pelo id passado no parâmetro
- Caso encontre, exclua a mesma do banco, coloque esta instrução em um bloco try/catch
- redirecione para a rota index

```
 public function destroy($id)
    {
        try {
            $unidade = Unidade::find($id);
            $unidade->delete();
            return redirect()->route("unidade.index")->with("msg_sucesso", "Registro Excluído com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }
```


## 2 - Testando o sistema
Teste o seu sistema, para que você tenha certeza que está tudo o ok, o sistema deverá:

- Listar todas as unidades
- Criar uma unidade nova
- Editar uma unidade selecionada
- Excluir uma unidade selecionada


# TABELA-BANCO-CONFIGURANDO-MODEL

<a href="https://mjailton.com.br/campus/conteudo/passo/1484/38478/674/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - model Banco
Crie o model Banco

### Comando de Criação
Para criar o model status use o comando:
```
php artisan make:model Banco -m
```


## 2 - migration bancos
adicione os seguintes campos:
- codigo varchar(25)
- banco varchar(80)

```
Schema::create('bancos', function (Blueprint $table) {
            $table->id();
            $table->string("codigo", 25);
            $table->string("banco", 80);
            $table->timestamps();
        });
```

## 3 - fillable Banco
Configure os fillables do Model Banco

```
protected $fillable=["id", "codigo", "banco"];
```

## 4 - BancoSeeder
Crie a seed Banco

### Comando de Criação
Para criar a seed Banco use o comando:

```
php artisan make:seed BancoSeeder
```

### Popular Dados

```
Banco::Create(['codigo' =>'999', 'banco' => 'Caixa Interno']);
        Banco::Create(['codigo' =>'001', 'banco' => 'Banco do Brasil S.A.']);
        Banco::Create(['codigo' =>'004', 'banco' => 'Banco do Nordeste do Brasil S.A.']);
        Banco::Create(['codigo' =>'033', 'banco' => 'Banco Santander (Brasil) S.A.']);
        Banco::Create(['codigo' =>'104', 'banco' => 'Caixa Econômica Federal']);
        Banco::Create(['codigo' =>'341', 'banco' => 'Itaú Unibanco S.A.']);
        Banco::Create(['codigo' =>'260', 'banco' => 'Nu Pagamentos S.A (Nubank)']);
        Banco::Create(['codigo' =>'290', 'banco' => 'Pagseguro Internet S.A']);
        Banco::Create(['codigo' =>'237', 'banco' => 'Banco Bradesco S.A.']);
        Banco::Create(['codigo' =>'246', 'banco' => 'Banco ABC Brasil S.A.']);
        Banco::Create(['codigo' =>'748', 'banco' => 'Banco Cooperativo Sicredi S.A.']);
        Banco::Create(['codigo' =>'117', 'banco' => 'Advanced Cc Ltda']);
        Banco::Create(['codigo' =>'121', 'banco' => 'Banco Agibank S.A.']);
        Banco::Create(['codigo' =>'172', 'banco' => 'Albatross Ccv S.A']);
        Banco::Create(['codigo' =>'188', 'banco' => 'Ativa Investimentos S.A']);
        Banco::Create(['codigo' =>'654', 'banco' => 'Banco A.J.Renner S.A.']);
        Banco::Create(['codigo' =>'246', 'banco' => 'Banco ABC Brasil S.A.']);
        Banco::Create(['codigo' =>'075', 'banco' => 'Banco ABN AMRO S.A']);
        Banco::Create(['codigo' =>'121', 'banco' => 'Banco Agibank S.A.']);
        Banco::Create(['codigo' =>'025', 'banco' => 'Banco Alfa S.A.']);
        Banco::Create(['codigo' =>'641', 'banco' => 'Banco Alvorada S.A.']);
        Banco::Create(['codigo' =>'065', 'banco' => 'Banco Andbank (Brasil) S.A.']);
        Banco::Create(['codigo' =>'213', 'banco' => 'Banco Arbi S.A.']);
        Banco::Create(['codigo' =>'096', 'banco' => 'Banco B3 S.A.']);
        Banco::Create(['codigo' =>'024', 'banco' => 'Banco BANDEPE S.A.']);
        Banco::Create(['codigo' =>'318', 'banco' => 'Banco BMG S.A.']);
        Banco::Create(['codigo' =>'752', 'banco' => 'Banco BNP Paribas Brasil S.A.']);
        Banco::Create(['codigo' =>'107', 'banco' => 'Banco BOCOM BBM S.A.']);
        Banco::Create(['codigo' =>'063', 'banco' => 'Banco Bradescard S.A.']);
        Banco::Create(['codigo' =>'036', 'banco' => 'Banco Bradesco BBI S.A.']);
        Banco::Create(['codigo' =>'122', 'banco' => 'Banco Bradesco BERJ S.A.']);
        Banco::Create(['codigo' =>'204', 'banco' => 'Banco Bradesco Cartões S.A.']);
        Banco::Create(['codigo' =>'394', 'banco' => 'Banco Bradesco Financiamentos S.A.']);
        Banco::Create(['codigo' =>'218', 'banco' => 'Banco BS2 S.A.']);
        Banco::Create(['codigo' =>'208', 'banco' => 'Banco BTG Pactual S.A.']);
        Banco::Create(['codigo' =>'336', 'banco' => 'Banco C6 S.A – C6 Bank']);
        Banco::Create(['codigo' =>'473', 'banco' => 'Banco Caixa Geral – Brasil S.A.']);
        Banco::Create(['codigo' =>'412', 'banco' => 'Banco Capital S.A.']);
        Banco::Create(['codigo' =>'040', 'banco' => 'Banco Cargill S.A.']);
        Banco::Create(['codigo' =>'368', 'banco' => 'Banco Carrefour']);
        Banco::Create(['codigo' =>'266', 'banco' => 'Banco Cédula S.A.']);
        Banco::Create(['codigo' =>'739', 'banco' => 'Banco Cetelem S.A.']);
        Banco::Create(['codigo' =>'233', 'banco' => 'Banco Cifra S.A.']);
        Banco::Create(['codigo' =>'745', 'banco' => 'Banco Citibank S.A.']);
        Banco::Create(['codigo' =>'241', 'banco' => 'Banco Clássico S.A.']);
        Banco::Create(['codigo' =>'756', 'banco' => 'Banco Cooperativo do Brasil S.A. ']);
        Banco::Create(['codigo' =>'748', 'banco' => 'Banco Cooperativo Sicredi S.A.']);
        Banco::Create(['codigo' =>'222', 'banco' => 'Banco Credit Agricole Brasil S.A.']);
        Banco::Create(['codigo' =>'505', 'banco' => 'Banco Credit Suisse (Brasil) S.A.']);
        Banco::Create(['codigo' =>'069', 'banco' => 'Banco Crefisa S.A.']);
        Banco::Create(['codigo' =>'003', 'banco' => 'Banco da Amazônia S.A.']);
        Banco::Create(['codigo' =>'083', 'banco' => 'Banco da China Brasil S.A.']);
        Banco::Create(['codigo' =>'707', 'banco' => 'Banco Daycoval S.A.']);
        Banco::Create(['codigo' =>'051', 'banco' => 'Banco de Desenvolvimento do Espírito Santo S.A.']);
        Banco::Create(['codigo' =>'300', 'banco' => 'Banco de La Nacion Argentina']);
        Banco::Create(['codigo' =>'495', 'banco' => 'Banco de La Provincia de Buenos Aires']);
        Banco::Create(['codigo' =>'335', 'banco' => 'Banco Digio S.A']);
        Banco::Create(['codigo' =>'047', 'banco' => 'Banco do Estado de Sergipe S.A.']);
        Banco::Create(['codigo' =>'037', 'banco' => 'Banco do Estado do Pará S.A.']);
        Banco::Create(['codigo' =>'041', 'banco' => 'Banco do Estado do Rio Grande do Sul S.A.']);
        Banco::Create(['codigo' =>'196', 'banco' => 'Banco Fair Corretora de Câmbio S.A']);
        Banco::Create(['codigo' =>'265', 'banco' => 'Banco Fator S.A.']);
        Banco::Create(['codigo' =>'224', 'banco' => 'Banco Fibra S.A.']);
        Banco::Create(['codigo' =>'626', 'banco' => 'Banco Ficsa S.A.']);
        Banco::Create(['codigo' =>'094', 'banco' => 'Banco Finaxis S.A.']);
        Banco::Create(['codigo' =>'612', 'banco' => 'Banco Guanabara S.A.']);
        Banco::Create(['codigo' =>'012', 'banco' => 'Banco Inbursa S.A.']);
        Banco::Create(['codigo' =>'604', 'banco' => 'Banco Industrial do Brasil S.A.']);
        Banco::Create(['codigo' =>'653', 'banco' => 'Banco Indusval S.A.']);
        Banco::Create(['codigo' =>'077', 'banco' => 'Banco Inter S.A.']);
        Banco::Create(['codigo' =>'249', 'banco' => 'Banco Investcred Unibanco S.A.']);
        Banco::Create(['codigo' =>'184', 'banco' => 'Banco Itaú BBA S.A.']);
        Banco::Create(['codigo' =>'029', 'banco' => 'Banco Itaú Consignado S.A.']);
        Banco::Create(['codigo' =>'479', 'banco' => 'Banco ItauBank S.A']);
        Banco::Create(['codigo' =>'376', 'banco' => 'Banco J. P. Morgan S.A.']);
        Banco::Create(['codigo' =>'074', 'banco' => 'Banco J. Safra S.A.']);
        Banco::Create(['codigo' =>'217', 'banco' => 'Banco John Deere S.A.']);
        Banco::Create(['codigo' =>'076', 'banco' => 'Banco KDB S.A.www.bancokdb.com.br']);
        Banco::Create(['codigo' =>'757', 'banco' => 'Banco KEB HANA do Brasil S.A.']);
        Banco::Create(['codigo' =>'600', 'banco' => 'Banco Luso Brasileiro S.A.']);
        Banco::Create(['codigo' =>'243', 'banco' => 'Banco Máxima S.A.']);
        Banco::Create(['codigo' =>'720', 'banco' => 'Banco Maxinvest S.A.']);
        Banco::Create(['codigo' =>'389', 'banco' => 'Banco Mercantil de Investimentos S.A.']);
        Banco::Create(['codigo' =>'389', 'banco' => 'Banco Mercantil do Brasil S.A.']);
        Banco::Create(['codigo' =>'370', 'banco' => 'Banco Mizuho do Brasil S.A.']);
        Banco::Create(['codigo' =>'746', 'banco' => 'Banco Modal S.A.']);
        Banco::Create(['codigo' =>'066', 'banco' => 'Banco Morgan Stanley S.A.']);
        Banco::Create(['codigo' =>'456', 'banco' => 'Banco MUFG Brasil S.A.www.br.bk.mufg.jp']);
        Banco::Create(['codigo' =>'007', 'banco' => 'Banco Nacional de Desenvolvimento Econômico e Social – BNDES']);
        Banco::Create(['codigo' =>'169', 'banco' => 'Banco Olé Bonsucesso Consignado S.A.']);
        Banco::Create(['codigo' =>'111', 'banco' => 'Banco Oliveira Trust Dtvm S.A']);
        Banco::Create(['codigo' =>'079', 'banco' => 'Banco Original do Agronegócio S.A.']);
        Banco::Create(['codigo' =>'212', 'banco' => 'Banco Original S.A.']);
        Banco::Create(['codigo' =>'712', 'banco' => 'Banco Ourinvest S.A.']);
        Banco::Create(['codigo' =>'623', 'banco' => 'Banco PAN S.A.']);
        Banco::Create(['codigo' =>'611', 'banco' => 'Banco Paulista S.A.']);
        Banco::Create(['codigo' =>'643', 'banco' => 'Banco Pine S.A.']);
        Banco::Create(['codigo' =>'658', 'banco' => 'Banco Porto Real de Investimentos S.A.']);
        Banco::Create(['codigo' =>'747', 'banco' => 'Banco Rabobank International Brasil S.A.']);
        Banco::Create(['codigo' =>'633', 'banco' => 'Banco Rendimento S.A.']);
        Banco::Create(['codigo' =>'741', 'banco' => 'Banco Ribeirão Preto S.A.']);
        Banco::Create(['codigo' =>'120', 'banco' => 'Banco Rodobens S.A.']);
        Banco::Create(['codigo' =>'422', 'banco' => 'Banco Safra S.A.']);
        Banco::Create(['codigo' =>'630', 'banco' => 'Banco Smartbank S.A.']);
        Banco::Create(['codigo' =>'637', 'banco' => 'Banco Sofisa S.A.www.sofisa.com.br']);
        Banco::Create(['codigo' =>'655', 'banco' => 'Banco Votorantim S.A.']);
        Banco::Create(['codigo' =>'610', 'banco' => 'Banco VR S.A.']);
        Banco::Create(['codigo' =>'119', 'banco' => 'Banco Western Union do Brasil S.A.']);
        Banco::Create(['codigo' =>'124', 'banco' => 'Banco Woori Bank do Brasil S.A.']);
        Banco::Create(['codigo' =>'348', 'banco' => 'Banco Xp S/A']);
        Banco::Create(['codigo' =>'081', 'banco' => 'BancoSeguro S.A.']);
        Banco::Create(['codigo' =>'021', 'banco' => 'BANESTES S.A. Banco do Estado do Espírito Santo']);
        Banco::Create(['codigo' =>'755', 'banco' => 'Bank of America Merrill Lynch Banco Múltiplo S.A.']);
        Banco::Create(['codigo' =>'268', 'banco' => 'Barigui Companhia Hipotecária']);
        Banco::Create(['codigo' =>'250', 'banco' => 'BCV – Banco de Crédito e Varejo S.A.']);
        Banco::Create(['codigo' =>'144', 'banco' => 'BEXS Banco de Câmbio S.A.']);
        Banco::Create(['codigo' =>'253', 'banco' => 'Bexs Corretora de Câmbio S/A']);
        Banco::Create(['codigo' =>'134', 'banco' => 'Bgc Liquidez Dtvm Ltda']);
        Banco::Create(['codigo' =>'017', 'banco' => 'BNY Mellon Banco S.A.']);
        Banco::Create(['codigo' =>'301', 'banco' => 'Bpp Instituição De Pagamentos S.A']);
        Banco::Create(['codigo' =>'126', 'banco' => 'BR Partners Banco de Investimento S.A.']);
        Banco::Create(['codigo' =>'070', 'banco' => 'BRB – Banco de Brasília S.A.']);
        Banco::Create(['codigo' =>'092', 'banco' => 'Brickell S.A. Crédito, Financiamento e Investimentow']);
        Banco::Create(['codigo' =>'173', 'banco' => 'BRL Trust Distribuidora de Títulos e Valores Mobiliários S.A.']);
        Banco::Create(['codigo' =>'142', 'banco' => 'Broker Brasil Cc Ltda']);
        Banco::Create(['codigo' =>'292', 'banco' => 'BS2 Distribuidora de Títulos e Valores Mobiliários S.A.']);
        Banco::Create(['codigo' =>'011', 'banco' => 'C.Suisse Hedging-Griffo Cv S.A (Credit Suisse)']);
        Banco::Create(['codigo' =>'288', 'banco' => 'Carol Distribuidora de Títulos e Valor Mobiliários Ltda']);
        Banco::Create(['codigo' =>'130', 'banco' => 'Caruana Scfi']);
        Banco::Create(['codigo' =>'159', 'banco' => 'Casa Credito S.A']);
        Banco::Create(['codigo' =>'016', 'banco' => 'Ccm Desp Trâns Sc E Rs']);
        Banco::Create(['codigo' =>'089', 'banco' => 'Ccr Reg Mogiana']);
        Banco::Create(['codigo' =>'114', 'banco' => 'Central Cooperativa De Crédito No Estado Do Espírito Santo']);
        Banco::Create(['codigo' =>'320', 'banco' => 'China Construction Bank (Brasil) Banco Múltiplo S.A.']);
        Banco::Create(['codigo' =>'477', 'banco' => 'Citibank N.A.']);
        Banco::Create(['codigo' =>'180', 'banco' => 'Cm Capital Markets Cctvm Ltda']);
        Banco::Create(['codigo' =>'127', 'banco' => 'Codepe Cvc S.A']);
        Banco::Create(['codigo' =>'163', 'banco' => 'Commerzbank Brasil S.A. – Banco Múltiplo']);
        Banco::Create(['codigo' =>'060', 'banco' => 'Confidence Cc S.A']);
        Banco::Create(['codigo' =>'098', 'banco' => 'Credialiança Ccr']);
        Banco::Create(['codigo' =>'010', 'banco' => 'Credicoamo']);
        Banco::Create(['codigo' =>'133', 'banco' => 'Cresol Confederação']);
        Banco::Create(['codigo' =>'182', 'banco' => 'Dacasa Financeira S/A']);
        Banco::Create(['codigo' =>'707', 'banco' => 'Banco Daycoval S.A.']);
        Banco::Create(['codigo' =>'487', 'banco' => 'Deutsche Bank S.A. – Banco Alemão']);
        Banco::Create(['codigo' =>'140', 'banco' => 'Easynvest – Título Cv S.A']);
        Banco::Create(['codigo' =>'149', 'banco' => 'Facta S.A. Cfi']);
        Banco::Create(['codigo' =>'285', 'banco' => 'Frente Corretora de Câmbio Ltda.']);
        Banco::Create(['codigo' =>'278', 'banco' => 'Genial Investimentos Corretora de Valores Mobiliários S.A.']);
        Banco::Create(['codigo' =>'138', 'banco' => 'Get Money Cc Ltda']);
        Banco::Create(['codigo' =>'064', 'banco' => 'Goldman Sachs do Brasil Banco Múltiplo S.A.']);
        Banco::Create(['codigo' =>'177', 'banco' => 'Guide Investimentos S.A. Corretora de Valores']);
        Banco::Create(['codigo' =>'146', 'banco' => 'Guitta Corretora de Câmbio Ltda']);
        Banco::Create(['codigo' =>'078', 'banco' => 'Haitong Banco de Investimento do Brasil S.A.']);
        Banco::Create(['codigo' =>'062', 'banco' => 'Hipercard Banco Múltiplo S.A.www.hipercard.com.br']);
        Banco::Create(['codigo' =>'189', 'banco' => 'HS Financeira S/A Crédito, Financiamento e Investimentos']);
        Banco::Create(['codigo' =>'269', 'banco' => 'HSBC Brasil S.A. – Banco de Investimento']);
        Banco::Create(['codigo' =>'271', 'banco' => 'IB Corretora de Câmbio, Títulos e Valores Mobiliários S.A.']);
        Banco::Create(['codigo' =>'157', 'banco' => 'Icap Do Brasil Ctvm Ltda']);
        Banco::Create(['codigo' =>'132', 'banco' => 'ICBC do Brasil Banco Múltiplo S.A.']);
        Banco::Create(['codigo' =>'492', 'banco' => 'ING Bank N.V.www.ing.com']);
        Banco::Create(['codigo' =>'139', 'banco' => 'Intesa Sanpaolo Brasil S.A. ']);
        Banco::Create(['codigo' =>'652', 'banco' => 'Itaú Unibanco Holding S.A.']);
        Banco::Create(['codigo' =>'488', 'banco' => 'JPMorgan Chase Bank, National Association']);
        Banco::Create(['codigo' =>'399', 'banco' => 'Kirton Bank S.A. – Banco Múltiplo']);
        Banco::Create(['codigo' =>'293', 'banco' => 'Lastro RDV Distribuidora de Títulos e Valores Mobiliários Ltda.']);
        Banco::Create(['codigo' =>'105', 'banco' => 'Lecca Crédito, Financiamento e Investimento S/A']);
        Banco::Create(['codigo' =>'145', 'banco' => 'Levycam Ccv Ltda']);
        Banco::Create(['codigo' =>'113', 'banco' => 'Magliano S.A']);
        Banco::Create(['codigo' =>'323', 'banco' => 'Mercado Pago – Conta Do Mercado Livre']);
        Banco::Create(['codigo' =>'128', 'banco' => 'MS Bank S.A. Banco de Câmbio']);
        Banco::Create(['codigo' =>'137', 'banco' => 'Multimoney Cc Ltda']);
        Banco::Create(['codigo' =>'014', 'banco' => 'Natixis Brasil S.A. Banco Múltiplo']);
        Banco::Create(['codigo' =>'191', 'banco' => 'Nova Futura Corretora de Títulos e Valores Mobiliários Ltda.']);
        Banco::Create(['codigo' =>'753', 'banco' => 'Novo Banco Continental S.A.']);
        Banco::Create(['codigo' =>'613', 'banco' => 'Omni Banco S.A.www.bancopecunia.com.br']);
        Banco::Create(['codigo' =>'613', 'banco' => 'Omni Banco S.A.www.omni.com.br']);
        Banco::Create(['codigo' =>'254', 'banco' => 'Paraná Banco S.A.']);
        Banco::Create(['codigo' =>'326', 'banco' => 'Parati – Crédito Financiamento e Investimento S.A.']);
        Banco::Create(['codigo' =>'174', 'banco' => 'Pernambucanas Financ S.A']);
        Banco::Create(['codigo' =>'100', 'banco' => 'Planner Corretora De Valores S.A']);
        Banco::Create(['codigo' =>'125', 'banco' => 'Plural S.A. – Banco Múltiplo']);
        Banco::Create(['codigo' =>'093', 'banco' => 'Pólocred Scmepp Ltda']);
        Banco::Create(['codigo' =>'108', 'banco' => 'Portocred S.A']);
        Banco::Create(['codigo' =>'283', 'banco' => 'Rb Capital Investimentos Dtvm Ltda']);
        Banco::Create(['codigo' =>'101', 'banco' => 'Renascenca Dtvm Ltda']);
        Banco::Create(['codigo' =>'270', 'banco' => 'Sagitur Corretora de Câmbio Ltda.']);
        Banco::Create(['codigo' =>'751', 'banco' => 'Scotiabank Brasil S.A. Banco Múltiplo']);
        Banco::Create(['codigo' =>'276', 'banco' => 'Senff S.A. – Crédito, Financiamento e Investimento']);
        Banco::Create(['codigo' =>'545', 'banco' => 'Senso Ccvm S.A']);
        Banco::Create(['codigo' =>'190', 'banco' => 'Servicoop']);
        Banco::Create(['codigo' =>'183', 'banco' => 'Socred S.A']);
        Banco::Create(['codigo' =>'299', 'banco' => 'Sorocred Crédito, Financiamento e Investimento S.A.']);
        Banco::Create(['codigo' =>'118', 'banco' => 'Standard Chartered Bank (Brasil) ']);
        Banco::Create(['codigo' =>'197', 'banco' => 'Stone Pagamentos S.A']);
        Banco::Create(['codigo' =>'095', 'banco' => 'Travelex Banco de Câmbio S.A.']);
        Banco::Create(['codigo' =>'143', 'banco' => 'Treviso Corretora de Câmbio S.A.']);
        Banco::Create(['codigo' =>'131', 'banco' => 'Tullett Prebon Brasil Cvc Ltda']);
        Banco::Create(['codigo' =>'129', 'banco' => 'UBS Brasil Banco de Investimento S.A.']);
        Banco::Create(['codigo' =>'91', 'banco' => 'Unicred Central Rs']);
        Banco::Create(['codigo' =>'136', 'banco' => 'Unicred Cooperativa']);
        Banco::Create(['codigo' =>'298', 'banco' => 'Vips Cc Ltda']);
        Banco::Create(['codigo' =>'102', 'banco' => 'Xp Investimentos S.A']);
```

### Configurar DatabaseSeeder
Incluir **BancoSeeder::class**

```
public function run(): void
    {
       $this->call([
           StatusSeeder::class,
           CategoriaSeeder::class,
           UnidadeSeeder::class,
           BancoSeeder::class,
       ]);
    }
```

# BANCO-LISTAGEM

<a href="https://mjailton.com.br/campus/conteudo/passo/1484/38484/675/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Criando o Controller
Crie um controller de recursos chamado Banco, para que o projeto fique mais organizado salve o controller numa pasta chamada Cadastro

### Comando de Criação

Para criar o controller use o comando:
```
php artisan make:controller \Cadastro\BancoController -r
```

### Método Index
No controller BancoController implemente o método index, o qual deverá:

- pegar a lista de bancoss e colocar um array
- chamar a view Banco/Index com o array criado com a lista de bancos

```
 public function index()
    {
        $dados["lista"] = Banco::get();
        return View("Cadastro.Banco.Index", $dados);
    }
```


## 2 - Criando a Rota
Crie uma rota resource setando para o controller BancoController

```
Route::resource("/banco", BancoController::class);
```

### Chamando a Rota
Localize no menu o local para chamar a rota banco.index

```
 <li><a href="{{ route('banco.index') }}">Banco</a></li>
```

## 3 - Criando a View
Crie a view para a listagem de banco

### Criando a View
Dentro da pasta resources/view crie uma pasta chamada de Cadastro e dentro de Cadastro crie uma outra chamada de Banco e dentro da pasta Banco crie um arquivo chamado Index.blade.php.

### Testando o Sistema
Execute seu sistema e pelo menu banco abre a página de listagem de banco.

## 4 - Listando dados do banco
Na view Index, faça os seguintes procedimentos:

- Faça o loop para receber os dados do banco e listar na tabela
- Configure o link para fazer a edição de um registro
- Configure o link para fazer a exclusão de um registro

```
@foreach ($lista as $l)
                                <tr>
                                    <td align="center">{{ $l->id }}</td>
                                    <td align="left">{{ $l->codigo }}</td>
                                    <td align="left">{{ $l->banco }}</td>
                                    <td align="center">
                                        <a href="{{ route('banco.edit', $l->id) }}"
                                            class="d-inline-flex gap-3 btn btn-outline-roxo btn-pequeno"><i
                                                class="fas fa-edit"></i>
                                            Editar</a>

                                        <a href="javascript:;"
                                            onclick="confirm('Tem Certeza?') ? document.getElementById('apagar{{ $l->id }}').submit() : '';"
                                            class="d-inline-flex gap-3 btn btn-outline-vermelho btn-pequeno">
                                            <i class="fas fa-trash-alt"></i>
                                            <form action="{{ route('banco.destroy', $l->id) }}" method="POST"
                                                id="apagar{{ $l->id }}">
                                                @method('DELETE')
                                                @csrf
                                            </form>

                                            Excluir
                                        </a>
                                    </td>
                                </tr>
                            @endforeach

```

# BANCO-INSERINDO

<a href="https://mjailton.com.br/campus/conteudo/passo/1484/38490/676/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Configurando Formulário
Configure os dados do formulário para inserção dos dados

### Configurando o form
Configure o elemento form da view Index, com as seguintes ações:

- Setar a rota banco.store na propriedade action do form
- Setar o método post na propriedade method do form
- implementar o helper @csrf dentro do form

```
<form action="{{ route('banco.store') }}" method="POST">
  @csrf
```

### Configurando os inputs
configure os input atribuindo a eles na propriedade name o nome igual ao que foi definido na criação da tabela,
também observe os tipos de dados específicos e os que são obrigatórios atribua a propriedade required.

```
 <form action="{{ route('banco.update', $banco->id) }}" method="POST">
        @csrf
               <div class="   p-2 pt-0 radius-4">
                            <div class="rows center-middle">
                                <div class="col-3">
                                    <label class="text-label d-block text-branco">Codigo </label>
                                    <input type="text" name="codigo" 
                                        class="form-campo">
                                </div>
                                <div class="col-6">
                                    <label class="text-label d-block text-branco">Nome </label>
                                    <input type="text" name="banco" 
                                        class="form-campo">
                                </div>
                                <div class="col-3 mt-0 pt-4">
                                    <input type="submit" value="Salvar" class="w-100 btn btn-roxo text-uppercase">
                                </div>
                            </div>
                        </div>
                    </div>
```

## 2 - Método store
implemente o método store para receber e salvar os dados do formulário no Banco de dados

### Salvando os dados
Implemente o método store de forma que o mesmo receba os dados do formulário e salve no banco de dados, caso ache necessário use um bloco try/catch

```
$req = $request->except(["_token"]);
        try {
            Banco::Create($req);
            return redirect()->route("banco.index")->with("msg_sucesso", "Registro Inserido com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
```

## 3 - Criando o request
Uma boa prática de programação é validar os dados antes de enviá-los para o banco de dados e uma bom recurso que o laravel oferece são os requests.
implemente um request de forma que faça todas as validações necessárias para salvar a informações no banco

### Comando de Criação
Para criar um request use os seguinte comando:

```
php artisan make:request BancoRequest
```

## 4 - BancoRequest
No método store troque o parâmetro Request para BancoRequest

```
public function store(BancoRequest $request)
    {
        $req = $request->except(["_token"]);
        try {
            Banco::Create($req);
            return redirect()->route("banco.index")->with("msg_sucesso", "Registro Inserido com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }
```

### Configuração do request
No arquivo de request configure as validações necessárias e não esqueça de setar o método authorize para true;

```
public function rules()
    {
        $id= $this->segment(2);
        return [
            "banco" => "required",
            "codigo" => "required"
        ];
    }

```

## 5 - Testando o sistema
Teste o sistema fazendo cadastros

# BANCO-ALTERANDO 

<a href="https://mjailton.com.br/campus/conteudo/passo/1484/38496/677/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Metodo Edit
Configure o método edit do Controller, com as seguinte ações:

- Busque a banco pelo id passado no parâmetro e guarde a informação em um array
- liste todas as bancos e guarde as informações em um array
- Chame a view Index, passando o array de dados como parâmetro

```
public function edit($id)
    {
        $dados["banco"] = Banco::find($id);
        $dados["lista"] = Banco::get();
        return View('Cadastro.Banco.Index', $dados);
    }
```

## 2 - Configurando Formulário
Configure os dados do formulário para ediçao dos dados

### Configurando o form
Configure o elemento form da view Index, com as seguintes ações:

- o sistema deve verificar se o objeto banco existe,
- caso ele exista, no formulário deve ser configurada a rota banco.update
- caso não exista, no formulário deve ser configurada a rota bancp.store

```
@if (isset($banco))
                        <form action="{{ route('banco.update', $banco->id) }}" method="POST">
                            @method('put')
                        @else
                            <form action="{{ route('banco.store') }}" method="POST">
                    @endif
                    @csrf
```

### Configure os inputs
na propriedade value de cada input, faça uma verificação se existe o objeto banco, se existir imprimir o valor do campo correspondente, senão existe imprimir o objeto old()

```
 <div class="{{ isset($banco->banco) ? 'bg-edit' : 'caixafield' }}  p-2 radius-4 border">
                        <div class="   p-2 pt-0 radius-4">
                            <div class="rows center-middle">
                                <div class="col-3">
                                    <label class="text-label d-block text-branco">Codigo </label>
                                    <input type="text" name="codigo" value="{{ $banco->codigo ?? old('cod') }}"
                                        class="form-campo">
                                </div>
                                <div class="col-6">
                                    <label class="text-label d-block text-branco">Nome </label>
                                    <input type="text" name="banco" value="{{ $banco->banco ?? old('banco') }}"
                                        class="form-campo">
                                </div>
                                <div class="col-3 mt-0 pt-4">
                                    <input type="submit" value="Salvar" class="w-100 btn btn-roxo text-uppercase">
                                </div>
                            </div>
                        </div>
                    </div>
```

### Método update
Implemente o método update de forma que o mesmo receba os dados do formulário e salve no banco de dados, caso ache necessário use um bloco try/catch

```
$req = $request->except(["_token", "_method"]);
        try {
            Banco::find($id)->update($req);
            return redirect()->route("banco.index")->with("msg_sucesso", "Registro Alterado com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
```

# BANCO-EXCLUSAO

<a href="https://mjailton.com.br/campus/conteudo/passo/1484/38502/677/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## 1 - Excluir
Faça o teste do seu sistema de forma que o mesmo consiga criar um novo registro e também alterá-lo

### Método destroy
implemente o método destroy do Controller, com as seguinte ações:

- Busque o banco pelo id passado no parâmetro
- Caso encontre, exclua o mesmo do banco, coloque esta instrução em um bloco try/catch
- redirecione para a rota index

```
public function destroy($id)
    {
        try {
            $banco = Banco::find($id);
            $banco->delete();
            return redirect()->route("banco.index")->with("msg_sucesso", "Registro Excluído com Sucesso");
        } catch (\Throwable $th) {
            return redirect()->back()->with("msg_erro", "Erro: " . $th->getMessage());
        }
    }
```

## 2 - Testando o sistema
Teste o seu sistema, para que você tenha certeza que está tudo o ok, o sistema deverá:

- Listar todos os bancos
- Criar um banco nova
- Editar um banco selecionada
- Excluir um banco selecionada


# TIPO-CC-CONFIGURANDO-MODEL

<a href="https://mjailton.com.br/campus/conteudo/passo/1485/38508/678/?f=2001" target="_blank">**Acesse o vídeo da aula aqui**</a>

## Configurando Model Tipo Conta Corrente

### 1 - model TipoContaCorrente

#### Crie o model TipoContaCorrente
```
php artisan make:model TipoContaCorrente -m
```

