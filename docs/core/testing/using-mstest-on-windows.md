---
title: Usar MSTest com o .NET Core no Windows
description: Como usar o MSTest com .NET Core no Windows usando o Visual Studio 2015
keywords: MSTest, .NET, .NET Core
author: ncarandini
ms.author: wiwagn
ms.date: 08/18/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: ed447641-3e85-4e50-b7ed-004630048a3e
translationtype: Human Translation
ms.sourcegitcommit: 90fe68f7f3c4b46502b5d3770b1a2d57c6af748a
ms.openlocfilehash: 94304cd742b63e77126bfa40651faa6974e58853
ms.lasthandoff: 03/03/2017

---

# <a name="unit-testing-with-mstest-and-net-core-on-windows-using-visual-studio-2015"></a>Testes de unidade com o MSTest com .NET Core no Windows usando o Visual Studio 2015

Embora o xUnit possa ser uma escolha melhor ao direcionar várias plataformas, também é possível usar o MSTest com o .NET Core no Windows.

## <a name="prerequisites"></a>Pré-requisitos

Siga as instruções na [Introdução ao .NET Core no Windows](../tutorials/using-on-windows.md) para criar o projeto de biblioteca.

### <a name="writing-the-test-project-using-mstest"></a>Escrever o projeto de teste usando MSTest

1. No Gerenciador de Soluções, abra o menu de contexto do nó **Solução** e escolha **Adicionar**, **Pasta Novo Projeto**. Nomeie a pasta como “test”. 
   Essa é apenas uma pasta de solução, não uma pasta física.

2. Abra o menu de contexto da pasta **test** e selecione **Adicionar**. **Novo Projeto**. Na caixa de diálogo **Novo Projeto**, escolha **Aplicativo de Console (.NET Core)**. Nomeie-o como "TestLibrary" e coloque-o explicitamente no caminho `Golden\test`. 

   > [!IMPORTANT]
   > O projeto deve ser um aplicativo de console, não uma biblioteca de classes.

3. No projeto **TestLibrary**, abra o menu de contexto do nó **Referências** e escolha **Adicionar Referência**. 

4. Na caixa de diálogo **Gerenciador de Referências**, marque **Biblioteca** em **Projetos**, no nó **Solução** e clique em **OK**. 

5. No projeto **TestLibrary**, abra o arquivo `project.json` e substitua `"Library": "1.0.0-*"` por `"Library": {"target": "project"}`. 

   Isso serve para evitar a resolução do projeto `Library` para um pacote NuGet com o mesmo nome. Definir explicitamente o destino como “project” garante que a ferramenta primeiro procurará por um projeto com esse nome e não por um pacote. 

6. Abra o menu de contexto para o nó **Referências** e escolha **Gerenciar Pacotes NuGet**.

7. Escolha “nuget.org” como a **Origem do pacote** e escolha a guia **Procurar**. Marque a caixa de seleção **Incluir pré-lançamento**, procure pelo **MSTest.TestFramework** versão 1.0.1-visualização ou mais recente e clique em **Instalar**. 

8. Procure pelo **dotnet-test-mstest** versão 1.1.1-visualização ou mais recente e clique em **Instalar**.

9. Edite `project.json` para adicionar `"testRunner": "mstest",` após a seção `"version"`.

10. Adicione um arquivo de classe `LibraryTests.cs` ao projeto **TestLibrary**, adicione as diretivas `using`, `Microsoft.VisualStudio.TestTools.UnitTesting;` e `using Library;`, na parte superior do arquivo e adicione o seguinte código à classe:
    ```csharp
    [TestClass]
    public class LibraryTests
    {
        [TestMethod]
        public void ThingGetsObjectValFromNumber()
        {
            Assert.AreEqual(42, new Thing().Get(42));
        }
    }
    ```
    * Opcionalmente, exclua o arquivo `Program.cs` do projeto **TestLibrary** e remova `"buildOptions": {"emitEntryPoint": true},` de `project.json`.

   Agora, você poderá criar a solução. 
   
11. No menu **Teste**, escolha **Windows**, **Gerenciador de Testes** e no Gerenciador de Testes, escolha **Executar Todos**.
   
   O teste deve ser aprovado.

