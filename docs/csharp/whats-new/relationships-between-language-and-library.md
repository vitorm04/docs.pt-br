---
title: "A relação entre os recursos de linguagem e tipos de biblioteca | Microsoft Docs"
description: "Recursos de linguagem geralmente dependem de tipos de biblioteca para implementação. Entenda a relação."
keywords: "Design de linguagem c#, biblioteca padrão"
author: billwagner
ms.author: wiwagn
ms.date: 07/20/2017
ms.topic: article
ms.prod: .net
ms.devlang: devlang-csharp
ms.openlocfilehash: 93fd26a72743fcf45df3904cb8d0c787d8a228a8
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="relationships-between-language-features-and-library-types"></a>Relações entre os recursos de linguagem e tipos de biblioteca

A definição de linguagem c# requer uma biblioteca padrão para determinados tipos e membros determinados acessíveis desses tipos. O compilador gera o código que usa esses tipos necessários e os membros de muitos recursos de idioma diferente. Quando necessário, há pacotes do NuGet que contêm os tipos necessários para as versões mais recentes do idioma ao escrever código para ambientes em que esses tipos ou membros não foram implantados ainda.

Essa dependência na funcionalidade de biblioteca padrão foi parte da linguagem c# desde sua primeira versão. Nessa versão, os exemplos incluídos:

* <xref:System.Exception>-usado para todas as exceções geradas pelo compilador.
* <xref:System.String>-C# `string` tipo é um sinônimo para <xref:System.String>.
* <xref:System.Int32>-sinônimo de `int`.

A primeira versão foi simple: o compilador e a biblioteca padrão fornecidos juntos e não havia somente uma versão de cada.

As versões subsequentes do c# ocasionalmente adicionou novos tipos ou membros para as dependências. Os exemplos incluem: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> e <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. C# 7.0 continua isso adicionando uma dependência no <xref:System.ValueTuple> para implementar o [tuplas](../tuples.md) recurso de idioma.

A equipe de design de linguagem funciona para minimizar a área de superfície dos tipos e membros necessários em uma biblioteca padrão compatível. Essa meta é equilibrada em relação a um design limpo onde novos recursos de biblioteca são incorporados diretamente para o idioma. Haverá novos recursos em versões futuras do c# que exigem novos tipos e membros em uma biblioteca padrão. É importante entender como gerenciar essas dependências em seu trabalho.

## <a name="managing-your-dependencies"></a>Gerenciando suas dependências

Ferramentas do compilador c# agora são desacopladas o ciclo de versão das bibliotecas do .NET em plataformas com suporte. Na verdade, bibliotecas .NET diferentes têm ciclos de lançamento diferentes: o .NET Framework no Windows é relesed como uma atualização do Windows, .NET Core é fornecido em uma agenda separada e as versões do Xamarin do envio de atualizações de biblioteca com as ferramentas Xamarin para cada plataforma de destino.

A maior parte do tempo, você não perceberá essas alterações. No entanto, quando você estiver trabalhando com uma versão mais recente do idioma que requer recursos não ainda nas bibliotecas do .NET nessa plataforma, você será referenciar os pacotes do NuGet para fornecer esses novos tipos.
Como as plataformas de seu aplicativo suporta é atualizadas com as novas instalações do framework, você pode remover a referência extra.

Essa separação significa que você pode usar os novos recursos de linguagem até mesmo quando você direcionar máquinas que podem não ter o framework correspondente.
