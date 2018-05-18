---
title: A relação entre os recursos de linguagem e os tipos de bibliotecas | Microsoft Docs
description: Os recursos de linguagem geralmente dependem dos tipos de bibliotecas para implementação. Entenda a relação.
ms.date: 07/20/2017
ms.openlocfilehash: dfae7972af0a251a92700d7d33bd6f971eb1870e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="relationships-between-language-features-and-library-types"></a>Relações entre os recursos de linguagem e os tipos de bibliotecas

A definição de linguagem C# exige que uma biblioteca padrão tenha determinados tipos e determinados membros acessíveis nesses tipos. O compilador gera o código que usa esses tipos e membros necessários para muitos recursos de linguagem diferentes. Quando necessário, há pacotes NuGet que contêm os tipos necessários para as versões mais recentes da linguagem ao escrever um código para ambientes em que esses tipos ou membros ainda não foram implantados.

Essa dependência da funcionalidade da biblioteca padrão faz parte da linguagem C# desde sua primeira versão. Nessa versão, os exemplos incluíam:

* <xref:System.Exception> – usado para todas as exceções geradas pelo compilador.
* <xref:System.String> – tipo `string` C# é um sinônimo de <xref:System.String>.
* <xref:System.Int32> – sinônimo de `int`.

A primeira versão era simples: o compilador e a biblioteca padrão eram fornecidos juntos e havia somente uma versão de cada um.

As versões posteriores do C# ocasionalmente adicionaram novos tipos ou membros às dependências. Os exemplos incluem: <xref:System.Runtime.CompilerServices.INotifyCompletion>, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> e <xref:System.Runtime.CompilerServices.CallerMemberNameAttribute>. O C# 7.0 continua isso adicionando uma dependência de <xref:System.ValueTuple> para implementar o recurso de linguagem de [tuplas](../tuples.md).

A equipe de design de linguagem trabalha para minimizar a área de superfície dos tipos e membros necessários em uma biblioteca padrão em conformidade. Essa meta é equilibrada em relação a um design limpo no qual novos recursos de biblioteca são incorporados diretamente na linguagem. Haverá novos recursos em versões futuras do C# que exigem novos tipos e membros em uma biblioteca padrão. É importante entender como gerenciar essas dependências em seu trabalho.

## <a name="managing-your-dependencies"></a>Gerenciando as dependências

As ferramentas do compilador C# agora são desacopladas do ciclo de liberação das bibliotecas .NET em plataformas com suporte. Na verdade, bibliotecas .NET diferentes têm ciclos de liberação diferentes: o .NET Framework no Windows é liberado como um Windows Update, o .NET Core é fornecido em um agendamento separado e as versões do Xamarin das atualizações de biblioteca são fornecidas com as ferramentas do Xamarin para cada plataforma de destino.

Na maior parte do tempo, você não perceberá essas alterações. No entanto, quando estiver trabalhando com uma versão mais recente da linguagem que exige recursos que ainda não estão nas bibliotecas .NET nessa plataforma, você referenciará os pacotes NuGet para fornecer esses novos tipos.
Conforme as plataformas para as quais seu aplicativo dá suporte forem atualizadas com as novas instalações de estrutura, você poderá remover a referência extra.

Essa separação significa que você pode usar os novos recursos de linguagem até mesmo quando direcionar computadores que podem não ter a estrutura correspondente.
