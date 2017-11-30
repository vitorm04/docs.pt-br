---
title: "Compilar uma solução completa do .NET Core no Windows usando o Visual Studio 2017"
description: "Saiba como compilar uma solução completa do .NET Core no Visual Studio 2017 no Windows."
keywords: .NET, .NET Core
author: bleroy
ms.author: mairaw
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ba7e082c-a7c8-431e-a342-f67734b660f6
ms.openlocfilehash: 694201c1a2a2c373f62b0e0d8e3c1d8aa7e6e881
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="building-a-complete-net-core-solution-on-windows-using-visual-studio-2017"></a>Compilar uma solução completa do .NET Core no Windows usando o Visual Studio 2017

O Visual Studio 2017 fornece um ambiente de desenvolvimento completo para desenvolver aplicativos .NET Core. Os procedimentos deste documento descrevem as etapas necessárias para criar uma solução típica do .NET Core que inclui bibliotecas reutilizáveis, testes e o uso de bibliotecas de terceiros. 

## <a name="prerequisites"></a>Pré-requisitos

Siga as instruções na [nossa página de pré-requisitos](../windows-prerequisites.md) para atualizar seu ambiente.

## <a name="a-solution-using-only-net-core-projects"></a>Uma solução que usa apenas projetos .NET Core

### <a name="writing-the-library"></a>Escrevendo a biblioteca

1. No Visual Studio, escolha **Arquivo**, **Novo** e **Projeto**. No **novo projeto** caixa de diálogo, expanda o **Visual C#** nó e escolha o **.NET padrão** nó e, em seguida, escolha **biblioteca de classes (.NET Standard)**. 

2. Nomeie o projeto como “Biblioteca” e a solução como “Dourada”. Deixe **Criar diretório para a solução** marcado. Clique em **OK**.

3. No Gerenciador de Soluções, abra o menu de contexto para o nó **Dependências** e escolha **Gerenciar Pacotes NuGet**.

4. Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**. Procure por **Newtonsoft.json**. Clique em **Instalar** e aceite o contrato de licença. O pacote deve aparecer sob **Dependências/NuGet** e ser restaurado automaticamente.

5. Renomeie o arquivo `Class1.cs` para `Thing.cs`. Aceite a renomeação da classe. Adicionar um método: `public int Get(int number) => Newtonsoft.Json.JsonConvert.DeserializeObject<int>($"{number}");`

7. No menu **Compilar**, escolha **Compilar Solução**.

   A solução deverá ser compilada sem erros.

### <a name="writing-the-test-project"></a>Escrevendo o projeto de teste

1. No Gerenciador de Soluções, abra o menu de contexto do nó **Solução** e escolha **Adicionar**, **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, em **Visual C# / .NET Core**, escolha **Projeto de Teste de Unidade (.NET Core)**. Nomeie-o como "TestLibrary" e clique em OK. 

2. No projeto **TestLibrary**, abra o menu de contexto do nó **Dependências** e escolha **Adicionar Referência**. Clique em **Projetos**, verifique o projeto de Biblioteca e clique em OK. Isso adiciona uma referência à biblioteca do projeto de teste.

3. Renomeie o arquivo `UnitTest1.cs` para `LibraryTests.cs` e aceite a renomeação de classe. Adicione `using Library;` à parte superior do arquivo e substitua o método `TestMethod1` com o código a seguir:
    ```csharp
    [TestMethod]
    public void ThingGetsObjectValFromNumber()
    {
        Assert.AreEqual(42, new Thing().Get(42));
    }
    ```

   Agora, você poderá criar a solução. 
   
4. No menu **Teste**, escolha **Windows**, **Gerenciador de Testes** para obter a janela Gerenciador de Testes na área de trabalho. Depois de alguns segundos, o teste `ThingGetsObjectValFromNumber` deve aparecer no gerenciador de testes. Escolha **Executar Todos**.
   
   O teste deve ser aprovado.

### <a name="writing-the-console-app"></a>Escrevendo o aplicativo de console

1. No Gerenciador de Soluções, abra o menu de contexto para a solução e adicione um novo projeto de **Aplicativo de Console (.NET Core)**. Nomeie como "Aplicativo".

2. No projeto **Aplicativo**, abra o menu de contexto do nó **Dependências** e escolha **Adicionar**, **Referência**. 

3. Na caixa de diálogo **Gerenciador de Referências**, marque **Biblioteca** em **Projetos**, no nó **Solução** e clique em **OK**

6. Abra o menu de contexto do nó **Aplicativo** e escolha **Definir como Projeto de Inicialização**. Isso garante que pressionar F5 ou CTRL+F5 iniciará o aplicativo de console.

7. Abra o arquivo `Program.cs`, adicione uma diretiva `using Library;` à parte superior do arquivo e adicione `Console.WriteLine($"The answer is {new Thing().Get(42)}.");` ao método `Main`.

8. Defina um ponto de interrupção após a linha que você acabou de adicionar.

9. Pressione F5 para executar o aplicativo.

   O aplicativo deve ser compilado sem erros e deve atingir o ponto de interrupção. Você também deve ser capaz de verificar se o aplicativo gera a saída "A resposta é 42".
