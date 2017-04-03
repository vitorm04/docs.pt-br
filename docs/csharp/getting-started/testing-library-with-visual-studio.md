---
title: Testar uma biblioteca de classes com .NET Core no Visual Studio 2017
description: Saiba como testar uma biblioteca de classes escrita em C# usando o Visual Studio 2017
keywords: .NET Core, biblioteca de classes .NET Standard, Visual Studio 2017, teste de unidade
author: stevehoag
ms.author: shoag
ms.date: 11/16/2016
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 069ad711-3eaa-45c6-94d7-b40249cc8b99
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: ee21799706b971f0ec13285b0771b32b4367f570
ms.lasthandoff: 03/13/2017

---

# <a name="testing-a-class-library-with-net-core-in-visual-studio-2017"></a>Testar uma biblioteca de classes com .NET Core no Visual Studio 2017 #

Em [Compilar uma biblioteca de classes com C# e .NET Core no Visual Studio 2017](library-with-visual-studio-2017.md), criamos uma biblioteca de classes simples que adiciona um método de extensão para a classe @System.String. Agora, criaremos um teste de unidade para ter certeza de que ela funciona conforme o esperado. Adicionaremos nosso projeto de teste de unidade à solução criada no tópico anterior.

## <a name="creating-a-unit-test-project"></a>Criar um projeto de teste de unidade ##

Para criar o projeto de teste de unidade, faça o seguinte:

1. No Gerenciador de Soluções, abra o menu de contexto do nó da solução **ClassLibraryProject** e escolha **Adicionar**, **Novo Projeto**.

   <!-- Need a VS 2017 version  [!NOTE] In addition to a Unit Test project, you can also use Visual Studio to create an XUnit test project for .NET Core. For a walkthrough that includes an XUnit test project, see [Getting started with .NET Core on Windows, using Visual Studio 2015](../../core/tutorials/using-on-windows.md). --> 

1. Na caixa de diálogo **Adicionar Novo Projeto**, expanda o nó **Visual C#** e o nó **.NET Core**, depois escolha o modelo de projeto **Projeto de Teste de Unidade (.NET Core)** e chame-o de `StringLibraryTest`, como mostra a figura a seguir.

   ![Image](./media/testproject.jpg)

1. Escolha o botão **OK** para criar o projeto. O Visual Studio cria o projeto e abre o arquivo `UnitTest1.cs` na janela do código, como mostra a figura a seguir.

   ![Image](./media/unit_test_code_window.jpg)

   O código-fonte criado pelo modelo de teste de unidade faz o seguinte:

   - Ele importa o namespace [Microsoft.VisualStudio.TestTools.UnitTesting](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.aspx), que contém os tipos usados para testes de unidade.

   - Ele aplica o atributo [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) à classe `UnitTest1`. Cada método de teste em uma classe de teste marcada com o atributo \[TestMethod\] será executado automaticamente quando o teste de unidade for executado.

   - Ele aplica o atributo [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) para definir `TestMethod1` como um método de teste para ser executado automaticamente quando o teste de unidade for executado.

1. No Gerenciador de Soluções, abra o menu de contexto para o nó **Dependencies** do projeto **StringLibraryTest** e escolha **Adicionar Referência**. Isso adiciona uma referência ao nosso projeto de biblioteca de classes, `StringLibrary`. 

1. Na caixa de diálogo **Gerenciador de Referências**, expanda o nó **Projetos** e escolha **Solução**, depois marque a caixa ao lado de **StringLibrary**, como mostra a figura a seguir. A adição de uma referência ao assembly `StringLibrary` permite que o compilador resolva chamadas para os métodos **StringLibrary**.

   ![Image](./media/add_reference.jpg)

1. Clique no botão **OK** para fechar a caixa de diálogo **Gerenciador de Referências**.

## <a name="adding-and-running-unit-test-methods"></a>Adicionar e executar métodos de teste de unidade ##

Quando o Visual Studio executa um teste de unidade, ele executa cada método marcado com o atributo [\[TestMethod\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testmethodattribute.aspx) em uma classe de teste de unidade (a classe à qual o atributo [\[TestClass\]](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.testclassattribute.aspx) é aplicado. Um método de teste termina quando a primeira falha é encontrada, ou quando todos os testes contidos no método tiverem êxito.

Os testes mais comuns chamam membros da classe [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx). Muitos métodos assert incluem pelo menos dois parâmetros, um deles é o resultado esperado do teste, e o outro é o resultado real do teste. Entre alguns de seus métodos chamados com mais frequência estão:

- `Assert.AreEqual`, que verifica se os dois valores ou objetos são iguais. A assert falha se os valores ou objetos não forem iguais.

- `Assert.AreSame`, que verifica se duas variáveis de objeto se referem ao mesmo objeto. A assert falhará se as variáveis se referirem a objetos diferentes.

- `Assert.IsFalse`, que verifica se uma condição é False. A assert falhará se a condição for True.

- `Assert.IsNotNull`, que verifica se um objeto não é `null`. A assert falhará se o objeto for `null`.

Além disso, o atributo [ \[ExpectedException\] ](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.expectedexceptionattribute.aspx) pode ser usado para indicar o tipo de exceção que um método de teste espera lançar. Use-o para testar as condições que devem resultar em uma exceção. O teste falhará se a exceção especificada não for lançada.

Ao testar o método `StringLibrary.StartsWithUpper`, queremos fornecer um número de cadeias de caracteres que comecem com um caractere maiúsculo. Esperamos que o método retorne `True` nesses casos, então podemos chamar o método [Assert.IsTrue(Boolean, String)](https://msdn.microsoft.com/library/ms243754.aspx). Da mesma forma, queremos fornecer um número de cadeias de caracteres que comecem com algo diferente de um caractere maiúsculo. Esperamos que o método retorne False nesses casos, então podemos chamar o método [Assert.IsFalse(Boolean, String)](https://msdn.microsoft.com/library/ms243805.aspx).

Como nosso método de biblioteca lida com cadeias de caracteres, também queremos ter certeza de que ele manipulará com êxito uma [cadeia de caracteres vazia](xref:System.String.Empty) (uma cadeia de caracteres válida sem caracteres e cujo @System.String.Length é 0) e uma cadeia de caracteres `null` (uma cadeia que não foi inicializada). Se `StartsWithUpper` for chamado como um método de extensão em uma instância de @System.String, ele não poderá receber uma cadeia de caracteres `null`. No entanto, também pode ser chamado diretamente como um método estático e receber um único argumento @System.String.

Definiremos três métodos, cada um deles chama seu método [Assert](https://msdn.microsoft.com/library/microsoft.visualstudio.testtools.unittesting.assert.aspx) repetidamente para cada elemento em uma matriz de cadeia de caracteres. Como o método de teste falha assim que encontra a primeira falha, chamaremos uma sobrecarga de método que nos permite passar uma cadeia de caracteres indicando o valor da cadeia de caracteres usado na chamada do método.

Para criar os métodos de teste:

1. Substitua o código na janela de código pelo seguinte:

   [!CODE-csharp[Teste1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/testlib1.cs#1)]

   Observe que nosso teste de caracteres maiúsculos no método `TestStartsWithUpper` inclui a letra maiúscula grega alfa (U+0391) e a letra maiúscula cirílica EM (U+041 C), e o teste de caracteres minúsculos no método `TestDoesNotStartWithUpper` inclui a letra minúscula grega alfa (U+03B1) e a letra minúscula cirílica Ghe (U+0433).

1. Na barra de menus, escolha **Arquivo**, **Salvar UnitTest1.cs como...**. Na caixa de diálogo **Salvar Arquivo como**, escolha a seta ao lado do botão **Salvar** e escolha **Salvar com Codificação...***.

1. Na caixa de diálogo Confirmar Salvar como, escolha o botão **Sim** para salvar o arquivo.

1. Na lista suspensa **Codificação** da caixa de diálogo **Opções Avançadas de Salvamento**, escolha **Unicode (UTF-8 com assinatura) - Página de código 65001** e escolha **OK**.

   Se você não salvar seu código-fonte em um arquivo codificado em UTF8, o Visual Studio poderá salvá-lo como um arquivo ASCII. Nesse caso, o tempo de execução não decodificará com precisão os caracteres fora do intervalo ASCII, e os resultados do teste não serão precisos.

1. Na barra de menus, escolha **Teste**, **Executar**, **Todos os Testes**. A janela **Gerenciador de Testes** deve ser aberta e mostrar que os dois testes foram executadas com êxito, como mostra a figura a seguir. Observe que os três testes estão listados na seção **Testes Aprovados**, e a seção **Resumo** relata o resultado da execução do teste.

   ![Image](./media/first_test.jpg)

## <a name="handling-test-failures"></a>Tratamento de falhas do teste ##

Nosso teste não apresentou falhas, então vamos alterá-lo um pouco para que um dos métodos do teste falhe:

1. Modifique a matriz `words` no método `TestDoesNotStartWithUpper` para incluir a cadeia de caracteres "Error", para que a instrução leia o seguinte:

   ```csharp
   string[] words = { "alphabet", "Error", "zebra", "abc", "αυτοκινητοβιομηχανία", "государство",
                      "1234", ".", ";", " " };
   ```

1. Execute o teste escolhendo **Teste**, **Executar**, **Todos os Testes**. Agora, a janela **Gerenciador de Teste** indica que dois testes tiveram êxito e um falhou, como mostra a figura a seguir.

   ![Image](./media/failed_test.jpg)

1. Escolha o teste com falha, `TestDoesNotStartWith`, na seção **Testes com Falha**. O painel inferior do **Gerenciador de Testes** exibe a mensagem produzida pela assert: "Assert.IsFalse falhou. Esperado para 'Error': false; real: True", como mostra a figura a seguir do **Gerenciador de Testes**. Devido à falha, todas as cadeias de caracteres na matriz após "Error" não foram testadas.

   ![Image](./media/failed_test2.jpg)

1. Remova o código que foi adicionado (`"Error", `) e execute o teste novamente. Agora ele deve passar.

## <a name="testing-the-release-version-of-the-library"></a>Testar a versão de lançamento da biblioteca ##

Estamos executando nossos testes na versão de Depuração da biblioteca. Agora que todos os nossos testes foram aprovados, e nós testamos adequadamente nossa biblioteca, devemos executar os testes mais uma vez na compilação de Lançamento da biblioteca. Vários fatores, incluindo as otimizações do compilador, podem produzir um comportamento diferente entre as compilações de Depuração e Lançamento.

Para testar a compilação de Lançamento:

1. Na barra de ferramentas do Visual Studio, altere a configuração de compilação de **Depurar** para **Lançamento**. A figura a seguir mostra uma parte da barra de ferramentas.

   ![Image](./media/lib_release.jpg)

1. No **Gerenciador de Soluções**, abra o menu de contexto para o nó do projeto **StringLibrary** e escolha **Compilação** para recompilar a biblioteca.

1. Execute novamente os testes de unidade escolhendo **Teste**, **Executar**, **Todos os Testes** no menu do Visual Studio. Todos os testes devem ser aprovados.

Agora que você concluiu o teste de sua biblioteca, a próxima etapa é disponibilizá-la aos chamadores. Você pode agrupá-la com um ou mais aplicativos, ou pode distribuí-la como um pacote do NuGet. Para saber como fazer isso, consulte [Consumo de uma biblioteca de classes .NET Standard](./consuming-library-with-visual-studio-2017.md).

