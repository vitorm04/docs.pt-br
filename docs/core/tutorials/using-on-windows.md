---
title: "Guia de Introdução ao .NET Core no Windows"
description: "Introdução ao .NET Core no Windows usando o Visual Studio 2015"
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: d743134a-08a3-4ff6-aab7-49f71f0568c3
translationtype: Human Translation
ms.sourcegitcommit: 54da8aebd64e86c064214074bc261f72c3b0aedc
ms.openlocfilehash: bf7bf944ebbf3c53ee6206f86e1a168111b54378

---

# <a name="getting-started-with-net-core-on-windows-using-visual-studio-2015"></a>Introdução ao .NET Core no Windows usando o Visual Studio 2015

por [Bertrand Le Roy](https://github.com/bleroy) e [Phillip Carter](https://github.com/cartermp)

O Visual Studio 2015 fornece um ambiente de desenvolvimento completo para desenvolver aplicativos .NET Core. Os procedimentos deste documento descrevem as etapas necessárias para criar uma série de soluções .NET Core típicas ou soluções que incluem componentes .NET Core, usando o Visual Studio. Os cenários incluem testes e o uso de bibliotecas de terceiros que não foram criadas explicitamente para a versão mais recente do .NET Core. 

## <a name="prerequisites"></a>Pré-requisitos

Siga as instruções na [nossa página de pré-requisitos](../windows-prerequisites.md) para atualizar seu ambiente.

## <a name="getting-started"></a>Guia de Introdução

As etapas a seguir definirão o Visual Studio 2015 para o desenvolvimento de .NET Core:

1. Abra o Visual Studio e, no menu **Arquivo**, escolha **Novo** e **Projeto**.

2. Na caixa de diálogo **Novo Projeto**, na lista **Modelos**, expanda o nó **Visual C#** e escolha **.NET Core**. Você verá três novos modelos de projeto para **Biblioteca de Classes (.NET Core)**, **Aplicativo de Console (.NET Core)** e **Aplicativo Web do ASP.NET Core (.NET Core)**.

<a name="a-solution-using-only-net-core-projects"></a>Uma solução que usa apenas projetos .NET Core
----------------------------------------

### <a name="writing-the-library"></a>Escrevendo a biblioteca

1. No Visual Studio, escolha **Arquivo**, **Novo** e **Projeto**. Na caixa de diálogo **Novo Projeto**, expanda o nó **Visual C#**, escolha o nó **.NET Core** e escolha **Biblioteca de Classes (.NET Core)**. 

2. Nomeie o projeto como “Biblioteca” e a solução como “Dourada”. Deixe **Criar diretório para a solução** marcado. Clique em **OK**.

3. No Gerenciador de Soluções, abra o menu de contexto para o nó **Referências** e escolha **Gerenciar Pacotes NuGet**.

4. Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**. Procure por **Newtonsoft.json**. Clique em **Instalar**. 

5. Abra o menu de contexto para o nó **Referências** e escolha **Restaurar Pacotes**.

6. Renomeie o arquivo `Class1.cs` para `Thing.cs`. Aceite a renomeação da classe. Remova o construtor e adicione um método: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. No menu **Compilar**, escolha **Compilar Solução**.

   A solução deverá ser compilada sem erros.

### <a name="writing-the-test-project"></a>Escrevendo o projeto de teste

1. No Gerenciador de Soluções, abra o menu de contexto do nó **Solução** e escolha **Adicionar**, **Pasta Novo Projeto**. Nomeie a pasta como “test”. 
   Essa é apenas uma pasta de solução, não uma pasta física.

2. Abra o menu de contexto da pasta **test** e selecione **Adicionar**. **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, escolha **Aplicativo de Console (.NET Core)**. Nomeie-o como "TestLibrary" e coloque-o explicitamente no caminho `Golden\test`. 

> [!IMPORTANT]
> O projeto deve ser um aplicativo de console, não uma biblioteca de classes.

3. No projeto **TestLibrary**, abra o menu de contexto do nó **Referências** e escolha **Adicionar Referência**. 

4. Na caixa de diálogo **Gerenciador de Referências**, marque **Biblioteca** em **Projetos**, no nó **Solução** e clique em **OK**. 

5. No projeto **TestLibrary**, abra o arquivo `project.json` e substitua `"Library": "1.0.0-*"` por `"Library": {"target": "project", "version": "1.0.0-*"}`. 

   Isso serve para evitar a resolução do projeto `Library` para um pacote NuGet com o mesmo nome. Definir explicitamente o destino como “project” garante que a ferramenta primeiro procurará por um projeto com esse nome e não por um pacote. 
   
6. No projeto **TestLibrary**, abra o menu de contexto do nó **Referências** e escolha **Restaurar Pacotes**.

7. Abra o menu de contexto para o nó **Referências** e escolha **Gerenciar Pacotes NuGet**.

8. Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**. Marque a caixa de seleção **Incluir pré-lançamento**, procure pelo **xUnit** versão 2.2.0 ou mais recente e clique em **Instalar**. 

9. Procure pelo **dotnet-test-mstest** versão 2.2.0 ou mais recente e clique em **Instalar**.

10. Edite `project.json` e substitua `"imports": "dnxcore50"` por `"imports": [ "dnxcore50", "portable-net45+win8" ]`. 

   Isso permite que as bibliotecas xunit sejam devidamente restauradas e usadas pelo projeto: essas bibliotecas foram compiladas para serem usadas com perfis portáteis que incluem “portable-net45+win8”, mas não .NET Core, que não existia quando foram criadas. O `import` alivia as verificações de versão das ferramentas no tempo de build. Agora você pode restaurar os pacotes sem erros.

11. Edite `project.json` para adicionar `"testRunner": "xunit",` após a seção `"frameworks"`.

12. Adicione um arquivo de classe `LibraryTests.cs` ao projeto **TestLibrary**, adicione as diretivas `using`, `using Xunit;` e `using Library;`, na parte superior do arquivo e adicione o seguinte código à classe:
    ```csharp
    [Fact]
    public void ThingGetsObjectValFromNumber() {
        Assert.Equal(42, new Thing().Get(42));
    }
    ```
    * Opcionalmente, exclua o arquivo `Program.cs` do projeto **TestLibrary** e remova `"buildOptions": {"emitEntryPoint": true},` de `project.json`.

   Agora, você poderá criar a solução. 
   
13. No menu **Teste**, escolha **Windows**, **Gerenciador de Testes** e no Gerenciador de Testes, escolha **Executar Todos**.
   
   O teste deve ser aprovado.

### <a name="writing-the-console-app"></a>Escrevendo o aplicativo de console

1. No Gerenciador de Soluções, abra o menu de contexto para a pasta `src` e adicione um novo projeto **Aplicativo de Console (.NET Core)**. Nomeie-o como “Aplicativo” e defina o local como `Golden\src`.

2. No projeto **Aplicativo**, abra o menu de contexto do nó **Referências** e escolha **Adicionar**, **Referência**. 

3. Na caixa de diálogo **Gerenciador de Referências**, marque **Biblioteca** em **Projetos**, no nó **Solução** e clique em **OK**

4. No projeto **Aplicativo**, abra o arquivo `project.json` e substitua `"Library": "1.0.0-*"` por `"Library": {"target": "project"}`.

5. Abra o menu de contexto para o nó **Referências** e escolha **Restaurar Pacotes**.

6. Abra o menu de contexto do nó **Aplicativo** e escolha **Definir como Projeto de Inicialização**.

7. Abra o arquivo `Program.cs`, adicione uma diretiva `using Library;` à parte superior do arquivo e adicione `Console.WriteLine($"The answer is {new Thing().Get(42)}");` ao método `Main`.

8. Defina um ponto de interrupção após a linha que você acabou de adicionar.

9. Pressione F5 para executar o aplicativo.

   O aplicativo deve ser compilado sem erros e deve atingir o ponto de interrupção. Você também deve ser capaz de verificar se o aplicativo gera a saída "A resposta é 42".

<a name="a-mixed-net-core-library-and-net-framework-application"></a>Uma combinação de biblioteca do .NET Core e aplicativo do .NET Framework
--------------------------------------------------------

Com base na solução obtida com o script anterior, execute as seguintes etapas:

1. No Gerenciador de Soluções, abra o arquivo `project.json` para o projeto **Biblioteca** e substitua `"frameworks": {
    "netstandard1.6" }` por `"frameworks": {
    "netstandard1.4" }`.

2. No projeto **Biblioteca**, abra o menu de contexto do nó **Referências** e escolha **Restaurar Pacotes**.

   A solução ainda deverá ser compilada e funcionar exatamente como antes: o teste deve ser aprovado e o aplicativo de console deve ser executável e depurável.

3. No projeto **Biblioteca**, abra o menu de contexto e escolha **Compilar**.

4. No Gerenciador de Soluções, abra o menu de contexto da pasta `src` e escolha **Adicionar**. , **Novo Projeto**.

5. Na caixa de diálogo **Novo Projeto**, escolha o nó **Visual C#** e **Aplicativo de Console**.

> [!IMPORTANT]
> Verifique se você escolheu um aplicativo de console padrão, não a versão do .NET Core. Nesta seção, você consumirá a biblioteca de um aplicativo do .NET Framework.

6. Nomeie o projeto como “FxApp” e defina o local como `Golden\src`.

7. No projeto **FxApp**, abra o menu de contexto do nó **Referências** e escolha **Adicionar Referência**.

8. Na caixa de diálogo **Gerenciador de Referências**, escolha **Procurar** e navegue até o local da compilação `Library.dll` (no caminho ...Golden\src\Library\bin\Debug\netstandard1.4) e clique em **Adicionar**. 

   Você também poderia empacotar a biblioteca e fazer referência ao pacote como outra forma de fazer referência de código .NET Core do .NET Framework.

9. Abra o menu de contexto para o nó **Referências** e escolha **Gerenciar Pacotes NuGet**.

10. Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**. Marque a caixa de seleção **Incluir pré-lançamento** e navegue para **Newtonsoft.json**. Clique em **Instalar**. 

11. No projeto **FxApp**, abra o arquivo `Program.cs` e adicione uma diretiva `using Library;` no topo do arquivo e adicione `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` ao método `Main` do programa.

12. Defina um ponto de interrupção após a linha que você acabou de adicionar.

13. Transforme **FxApp** no aplicativo de inicialização para a solução.

14. Pressione F5 para executar o aplicativo.

   O aplicativo deve ser compilado e atingir o ponto de interrupção. A saída do aplicativo deve ser "A resposta é 42.".
   
   > [!TIP]
   > Na plataforma Windows, você pode usar o MSTest. Saiba mais no [documento Usando o MSTest no Windows](../testing/using-mstest-on-windows.md).

<a name="moving-a-library-from-netstandard-14-to-13"></a>Mover uma biblioteca de netstandard 1.4 para 1.3
--------------------------------------------

1. No Gerenciador de Soluções, abra o arquivo `project.json` para o projeto **Biblioteca**.

2. Substitua `frameworks": { "netstandard1.4" }` por `frameworks": { "netstandard1.3" }`.

3. No projeto **Biblioteca**, abra o menu de contexto do nó **Referências** e escolha **Restaurar Pacotes**.

4. No menu **Compilar**, escolha **Compilar Biblioteca**.

5. Remova a referência `Library` do **FxApp** e adicione-o usando o caminho ...Golden\src\Library\bin\Debug\netstandard1.3. Ela agora fará referência à versão 1.3.

6. Pressione F5 para executar o aplicativo.

   Tudo deverá continuar a funcionar como antes. Verifique se a saída do aplicativo é “A resposta é 42.”, se o ponto de interrupção foi atingido e se as variáveis podem ser inspecionados.

<a name="a-mixed-pcl-library-and-net-framework-application"></a>Uma combinação de biblioteca de PCL e aplicativo do .NET Framework
--------------------------------------------------

Feche a solução anterior se ela estiver aberta: você começará um novo script a partir dessa seção.

### <a name="writing-the-library"></a>Escrevendo a biblioteca

1. No Visual Studio, escolha **Arquivo**, **Novo** e **Projeto**. Na caixa de diálogo **Novo Projeto**, expanda o nó **Visual C#** e escolha **Biblioteca de Classes (Portátil para iOS, Android e Windows)**. 

2. Nomeie o projeto como “PCLLibrary” e a solução como “GoldenPCL”. Deixe **Criar diretório para a solução** marcado. Clique em **OK**.

3. No Gerenciador de Soluções, abra o menu de contexto para o nó **Referências** e escolha **Gerenciar Pacotes NuGet**.

4. Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**. Marque a caixa de seleção **Incluir pré-lançamento** e navegue para **Newtonsoft.json**. Clique em **Instalar**. 

5. Renomeie a classe como “Thing” e adicione um método: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

6. No menu **Compilar**, escolha **Compilar Solução** e verifique se a solução é compilada.

### <a name="writing-the-console-app"></a>Escrevendo o aplicativo de console

1. No Gerenciador de Soluções, abra o menu de contexto do nó **Solução “GoldenPCL”** e escolha **Adicionar**. **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, expanda o nó **Visual C#**, escolha **Aplicativo de Console** e nomeie o projeto como “Aplicativo”. 

2. No projeto **Aplicativo**, abra o menu de contexto do nó **Referências** e escolha **Adicionar**, **Referência**. 

3. Na caixa de diálogo **Gerenciador de Referências**, escolha **Procurar** e navegue até o local da compilação `PCLLibrary.dll` (no caminho ..\GoldenPCL\PCLLibrary\bin\Debug) e clique em **Adicionar**. 

4. No projeto **Aplicativo**, abra o arquivo `Program.cs` e adicione uma diretiva `using PCLLibrary;` no topo do arquivo e adicione `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` ao método `Main` do programa.

5. Defina um ponto de interrupção após a linha que você acabou de adicionar.

6. No Gerenciador de Soluções, abra o menu de contexto do nó **Aplicativo** e escolha **Definir como Projeto de Inicialização**.

7. Pressione F5 para executar o aplicativo.

   O aplicativo deve ser compilado, executado e atingir o ponto de interrupção depois de gerar “A resposta é 42.”.

<a name="moving-a-pcl-to-a-netstandard-library"></a>Movendo uma PCL para uma biblioteca NetStandard
-------------------------------------
As ferramentas da Biblioteca de Classes Portátil podem modificar automaticamente sua PCL para direcionar .NET Standard. 

1.  Clique duas vezes no nó “Propriedades” para abrir a página Propriedade do Projeto

2.  Em “Cabeçalho de direcionamento”, clique no hiperlink “Direcionar para .NET Platform Standard”

3.  Clique em “Sim” quando a confirmação for solicitada

As ferramentas selecionarão automaticamente a versão do .NET Standard que inclui todos os destinos originalmente direcionados pelo seu PCL. Você pode direcionar uma versão diferente do .NET Standard usando o menu suspenso .NET Standard na página de propriedades do projeto.
 
* Se você já tinha um packages.config, será necessário desinstalar todos os pacotes instalados antes da conversão.

### <a name="manually-edit-projectjson-to-target-net-standard-from-an-existing-portable-class-library"></a>Edite manualmente o project.json para ser direcionado para o .NET Standard de uma Biblioteca de Classes Portátil existente

1.  Se seu project.json contiver “dnxcore50” no elemento “supports”, remova-o.

2.  Remova a dependência em “Microsoft.NETCore”

3.  Modifique a dependência em “Microsoft.NETCore.Portable.Compatibility” versão “1.0.0” para a versão “1.0.1”

4.  Adicione uma dependência em “NETStandard.Library” versão “1.6.0”

5.  No elemento “frameworks”, remova a estrutura “dotnet” (e o elemento “imports” dentro dele)

6.  Adicione ` "netstandard1.x” : { } ` ao elemento de estruturas, no qual x é substituído pela versão do .NET Standard de destino

### <a name="example-projectjson"></a>Exemplo de project.json

Este project.json inclui cláusulas de suporte para UWP e .NET 4.6 e é direcionado para o netstandard1.3:
```
{
  "supports": {
    "net46.app": {},
    "uwp.10.0.app": {},
  },
  "dependencies": {
    "NETStandard.Library": "1.6.0",
    "Microsoft.NETCore.Portable.Compatibility": "1.0.1"
  },
  "frameworks": {
    "netstandard1.3" : {}
  }
}
```





<!--HONumber=Nov16_HO4-->


