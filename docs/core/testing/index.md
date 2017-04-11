---
title: Teste de Unidade no .NET Core
description: Teste de Unidade no .NET Core
keywords: .NET, .NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 815ac74c-4bd9-4a94-a87c-78288b27c0e2
translationtype: Human Translation
ms.sourcegitcommit: 095ebad90e3f0b188d208d22f6f16b9552f8ea86
ms.openlocfilehash: ca9d57a3ef3382c4957de5edb55959f1a3f13ee0
ms.lasthandoff: 04/05/2017

---

# <a name="unit-testing-in-net-core"></a>Teste de Unidade no .NET Core

Por [Steve Smith](http://ardalis.com) e [Bill Wagner](https://github.com/BillWagner)

O .NET Core foi projetado com a capacidade de realizar testes em mente, para que a criação de testes de unidade para seus aplicativos seja mais fácil do que nunca. Este artigo apresenta brevemente os testes de unidade (e como eles diferem de outros tipos de testes).
Recursos vinculados demonstram como adicionar um projeto de teste à sua solução e executar testes de unidade usando a linha de comando ou o Visual Studio.

## <a name="getting-started-with-testing"></a>Introdução aos Testes
 
Ter um pacote de testes automatizados é uma das melhores maneiras de garantir que um aplicativo de software faça o que seus autores pretendiam. Há muitos tipos diferentes de testes diferentes para aplicativos de software, incluindo testes de integração, testes da Web, testes de carga e muitos outros. O nível mais baixo são os testes de unidade, que testam métodos ou componentes de software individuais. Testes de unidade só devem testar o código sob o controle do desenvolvedor e não questões de infraestrutura, como bancos de dados, sistemas de arquivos ou recursos de rede. Testes de unidade podem ser escritos usando [TDD (Desenvolvimento Orientado por Testes)](http://deviq.com/test-driven-development/) ou adicionados ao código existente para confirmar sua precisão. Em ambos os casos, eles devem ser pequenos, bem nomeados e rápidos, visto que o ideal é ser capaz de executar centenas deles antes de enviar as alterações por push para o repositório de código compartilhado do projeto.

> [!NOTE]
> Os desenvolvedores geralmente enfrentam problemas para inventar bons nomes para seus métodos e classe de teste. Como ponto de partida, a equipe de produto do ASP.NET segue [essas convenções](https://github.com/aspnet/Home/wiki/Engineering-guidelines#unit-tests-and-functional-tests).

Ao escrever testes de unidade, tenha cuidado para não apresentar dependências à infraestrutura acidentalmente. Eles tendem a tornar os testes mais lentos e mais frágeis, ficando reservados aos testes de integração. Você pode evitar essas dependências ocultas no código do aplicativo seguindo o [Princípio de Dependências Explícitas](http://deviq.com/explicit-dependencies-principle/) e usando a [Injeção de Dependência](https://docs.microsoft.com/en-us/aspnet/core/fundamentals/dependency-injection) para solicitar as dependências da estrutura. Você pode manter seus testes de unidade em um projeto separado dos seus testes de integração e verificar se o projeto de teste de unidade não tem dependências ou referências a pacotes de infraestrutura.

Saiba mais sobre testes de unidade em projetos do .NET Core:

Experimente seguir o [passo a passo para criar testes de unidade com xUnit e a CLI do .NET](unit-testing-with-dotnet-test.md). 

A equipe do XUnit criou um tutorial que mostra [como usar o xUnit com o .NET Core e Visual Studio](http://xunit.github.io/docs/getting-started-dotnet-core.html).

Se você preferir usar o MSTest, tente as [instruções passo a passo para criar testes de unidade com o MSTest e a CLI do .NET](unit-testing-with-mstest.md).

