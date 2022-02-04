# Criando primeiro aplicativo Blazor

## Passos:

- [Instalar SDK do .NET](https://docs.microsoft.com/dotnet/core/install/linux?WT.mc_id=dotnet-35129-website)

    SDK: Kit de Desenvolvimento de Software.

## Verificando se a instalação foi bem sucedida
>Terminal
~~~
    dotnet
~~~
>Terminal

Se a instalação foi bem sucedida verá ao parecido com:
~~~
Usage: dotnet [options]
Usage: dotnet [path-to-application]

Options:
  -h|--help         Display help.
  --info            Display .NET information.
  --list-sdks       Display the installed SDKs.
  --list-runtimes   Display the installed runtimes.

path-to-application:
  The path to an application .dll file to execute.
~~~
## Criando app 
>Terminal
~~~
dotnet new blazorserver -o BlazorApp --no-https
~~~
Dê uma olhada rápida no conteúdo do BlazorAppdiretório. Vários arquivos foram criados no BlazorAppdiretório, para fornecer um aplicativo Blazor simples que está pronto para ser executado.

Program.csé o ponto de entrada para o aplicativo que inicia o servidor e onde você configura os serviços do aplicativo e o middleware.
App.razoré o componente raiz do aplicativo.
O Pagesdiretório contém algumas páginas da Web de exemplo para o aplicativo.
BlazorApp.csprojdefine o projeto do aplicativo e suas dependências.
O launchSettings.jsonarquivo dentro do Propertiesdiretório define diferentes configurações de perfil para o ambiente de desenvolvimento local. Um número de porta variando entre 5000-5300 é atribuído automaticamente na criação do projeto e salvo neste arquivo.

## Executando

O "dotnet watch" comando compilará e iniciará o aplicativo e, em seguida, atualizará o aplicativo sempre que você fizer alterações no código. Você pode interromper o aplicativo a qualquer momento selecionando Ctrl+ C.


>Terminal
~~~
    dotnet watch
~~~
O site abrirá no seu navegador!
![Site](https://github.com/neresfabio/estudo.NET/blob/master/Blazor_Tutorial/BlazorApp/images/Captura%20de%20tela%20de%202022-02-03%2020-45-36.png)

## Componentes

>Counter: por padrão no layout inicial temos um botão que conta as vezes que o mesmo foi precionado.

No diretorio/pasta "Pages" esta o componente Counter.razor

>Crie um novo componente no Index.razor, pode ser ali pela linha 11.

~~~
<Counter/>
~~~

## Modificar o componente
Os parâmetros do componente são especificados usando atributos ou conteúdo filho, que permitem definir propriedades no componente filho. Defina um parâmetro no Countercomponente para especificar quanto ele incrementa a cada clique de botão:

Adicione uma propriedade pública para IncrementAmountcom um [Parameter]atributo.
Altere o IncrementCountmétodo para usar o IncrementAmountao incrementar o valor de currentCount.
O código a seguir mostra como conseguir isso. As linhas destacadas mostram as alterações.

~~~
@page "/counter"

<PageTitle>Counter</PageTitle>

<h1>Counter</h1>

<p>Current count: @currentCount</p>

<button class="btn btn-primary" @onclick="IncrementCount">Click me</button>

@code {
    private int currentCount = 0;

    [Parameter]
    public int IncrementAmount { get; set; } = 1;

    private void IncrementCount()
    {
        currentCount += IncrementAmount;
    }
} 
~~~

Agora no "Index.razor", atualize o "Counter" elemento para adicionar um "IncrementAmountatributo" que altera o valor do incremento para dez, conforme mostrado pela linha destacada no código a seguir:

~~~ 
<Counter IncrementAmount = "10"/> 
~~~

O Index componente agora tem seu próprio contador que é incrementado em dez cada vez que o botão Clique em mim é selecionado, conforme mostrado na imagem a seguir. O Counter componente ( Counter.razor) em /countercontinua a aumentar em um.






