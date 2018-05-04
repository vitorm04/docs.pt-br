---
title: Teste de Unidade no .NET Core
description: Testes de unidade nunca foram tão fáceis. Saiba como usar o teste de unidade em projetos do .NET Core e .NET Standard.
author: ardalis
ms.author: wiwagn
ms.date: 08/30/2017
ms.openlocfilehash: b3d8393cf285eae3493328b16c3dc038af208da6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="unit-testing-in-net-core-and-net-standard"></a>Teste de unidade no .NET Core e .NET Standard

O .NET Core foi projetado com a capacidade de realizar testes em mente, para que a criação de testes de unidade para seus aplicativos seja mais fácil do que nunca. Este artigo apresenta brevemente os testes de unidade (e como eles diferem de outros tipos de testes). Os recursos vinculados demonstram como adicionar um projeto de teste à sua solução e executar testes de unidade usando a linha de comando ou o Visual Studio.

O .NET Core 2.0 suporta o [.NET Standard 2.0](../../standard/net-standard.md). As bibliotecas usadas para demonstrar os testes de unidade nesta seção contam com o .NET Standard e também funcionarão em outros tipos de projeto.

Começando no .NET Core 2.0, há modelos de projeto de teste de unidade para Visual Basic e F#, bem como para C#.

## <a name="getting-started-with-testing"></a>Introdução aos Testes

Ter um pacote de testes automatizados é uma das melhores maneiras de garantir que um aplicativo de software faça o que seus autores pretendiam. Há diferentes tipos de teste para aplicativos de software, incluindo testes de integração, testes da Web, testes de carga e muitos outros. Os testes de unidade que testam métodos ou componentes de software individuais são os testes de nível mais baixo. Testes de unidade só devem testar o código sob o controle do desenvolvedor e não questões de infraestrutura, como bancos de dados, sistemas de arquivos ou recursos de rede. Testes de unidade podem ser escritos usando [TDD (Desenvolvimento Orientado por Testes)](http://deviq.com/test-driven-development/) ou adicionados ao código existente para confirmar sua precisão. Em ambos os casos, eles devem ser pequenos, bem nomeados e rápidos, visto que o ideal é ser capaz de executar centenas deles antes de enviar as alterações por push para o repositório de códigos compartilhado do projeto.

> [!NOTE]
> Os desenvolvedores geralmente enfrentam problemas para inventar bons nomes para seus métodos e classe de teste. Como ponto de partida, a equipe de produto do ASP.NET segue [essas convenções](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Ao escrever testes de unidade, tenha cuidado para não apresentar dependências à infraestrutura acidentalmente. Eles tendem a tornar os testes mais lentos e mais frágeis, ficando reservados aos testes de integração. Você pode evitar essas dependências ocultas no código do aplicativo seguindo o [Princípio de Dependências Explícitas](http://deviq.com/explicit-dependencies-principle/) e usando a [Injeção de Dependência](/aspnet/core/fundamentals/dependency-injection) para solicitar as dependências da estrutura. Você pode manter seus testes de unidade em um projeto separado dos seus testes de integração e verificar se o projeto de teste de unidade não tem dependências ou referências a pacotes de infraestrutura.

Saiba mais sobre testes de unidade em projetos do .NET Core:

Os projetos de Teste de Unidade para .NET Core são suportados para [C#](../../csharp/index.md), [F#](../../fsharp/index.md) e [Visual Basic](../../visual-basic/index.md). Também é possível escolher entre [xUnit](http://xunit.github.io), [NUnit](http://nunit.org) e [MSTest](https://github.com/Microsoft/vstest-docs).

Você pode ler sobre as combinações nestes artigos passo a passo:

* Criar testes de unidade usando [*XUnit* e *C#* com a CLI do .NET Core](unit-testing-with-dotnet-test.md).
* Criar testes de unidade usando [*NUnit* e *C#* com a CLI do .NET Core](unit-testing-with-nunit.md).
* Criar testes de unidade usando [*MSTest* e *C#* com a CLI do .NET Core](unit-testing-with-mstest.md).
* Criar testes de unidade usando [*XUnit* e *F#* com a CLI do .NET Core](unit-testing-fsharp-with-dotnet-test.md).
* Criar testes de unidade usando [*NUnit* e *F#* com a CLI do .NET Core](unit-testing-fsharp-with-nunit.md).
* Criar testes de unidade usando [*MSTest* e *F#* com a CLI do .NET Core](unit-testing-fsharp-with-mstest.md).
* Criar testes de unidade usando [*XUnit* e *Visual Basic* com a CLI do .NET Core](unit-testing-visual-basic-with-dotnet-test.md).
* Criar testes de unidade usando [*NUnit* e *Visual Basic* com a CLI do .NET Core](unit-testing-visual-basic-with-nunit.md).
* Criar testes de unidade usando [*MSTest* e *Visual Basic* com a CLI do .NET Core](unit-testing-visual-basic-with-mstest.md).

É possível escolher idiomas diferentes para as bibliotecas de classe e as bibliotecas de teste de unidade. Você pode aprender como combinando e correspondendo os passo a passos mencionados acima.

* O Visual Studio Enterprise oferece excelentes ferramentas de teste para o .NET Core. Para saber mais confira o [Live Unit Testing](/visualstudio/test/live-unit-testing) ou a [cobertura de código](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md#working-with-code-coverage).
* Para obter informações adicionais e exemplos de como usar a filtragem de teste de unidade, confira [Executando testes de unidade seletivos](selective-unit-tests.md) ou [including and excluding tests with Visual Studio](/visualstudio/test/live-unit-testing#including-and-excluding-test-projects-and-test-methods) (Incluindo e excluindo testes com o Visual Studio).
* A equipe do XUnit criou um tutorial que mostra [como usar o xUnit com o .NET Core e Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).
