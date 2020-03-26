---
title: 'Como: Inspecionar o conteúdo do conjunto usando metadadosLoadContext'
description: Saiba como usar metadataLoadContext, que é uma API que permite carregar conjuntos .NET para fins de inspeção.
author: MSDN-WhiteKnight
ms.date: 03/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: a782b2db4fb62cfaedaa6768e2131bda6bec864c
ms.sourcegitcommit: b75a45f0cfe012b71b45dd9bf723adf32369d40c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80229297"
---
# <a name="how-to-inspect-assembly-contents-using-metadataloadcontext"></a>Como: Inspecionar o conteúdo do conjunto usando metadadosLoadContext

A API de reflexão no .NET por padrão permite que os desenvolvedores inspecionem o conteúdo dos conjuntos carregados no contexto principal de execução. No entanto, às vezes não é possível carregar um conjunto no contexto de execução, por exemplo, porque ele foi compilado para outra plataforma ou arquitetura de processador, ou é um conjunto de [referência](reference-assemblies.md). A <xref:System.Reflection.MetadataLoadContext?displayProperty=fullName> API permite carregar e inspecionar tais conjuntos. Os conjuntos carregados no <xref:System.Reflection.MetadataLoadContext> são tratados apenas como metadados, ou seja, você pode examinar os tipos no conjunto, mas não pode executar nenhum código contido nele. Ao contrário do contexto <xref:System.Reflection.MetadataLoadContext> de execução principal, o não carrega automaticamente dependências do diretório atual; em vez disso, ele usa <xref:System.Reflection.MetadataAssemblyResolver> a lógica de vinculação personalizada fornecida pelo passado para ele.

## <a name="prerequisites"></a>Pré-requisitos

Para <xref:System.Reflection.MetadataLoadContext>usar, instale o pacote [System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext) NuGet. Ele é suportado em qualquer quadro de destino compatível com .NET Standard 2.0, por exemplo, .NET Core 2.0 ou .NET Framework 4.6.1.

## <a name="create-metadataassemblyresolver-for-metadataloadcontext"></a>Criar metadadosResolveresolver para MetadataLoadContext

Criando <xref:System.Reflection.MetadataLoadContext> as obrigações fornecendo a instância do <xref:System.Reflection.MetadataAssemblyResolver>. A maneira mais simples de fornecer <xref:System.Reflection.PathAssemblyResolver>um é usar o , que resolve assembléias a partir da coleção dada de strings de caminho de montagem. Esta coleção, além de montagens que você deseja inspecionar diretamente, também deve incluir todas as dependências necessárias. Por exemplo, para ler o atributo personalizado localizado em um conjunto externo, você deve incluir esse conjunto ou uma exceção será lançada. Na maioria dos casos, você deve incluir pelo menos o *conjunto central,* ou <xref:System.Object?displayProperty=nameWithType>seja, o conjunto contendo tipos de sistema incorporados, tais como . O código a seguir <xref:System.Reflection.PathAssemblyResolver> mostra como criar o uso da coleção que consiste no conjunto inspecionado e no conjunto central do tempo de execução atual:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CoreAssembly)]

Se você precisar de acesso a todos os tipos de BCL, você pode incluir todos os conjuntos de tempo de execução na coleção. O código a seguir <xref:System.Reflection.PathAssemblyResolver> mostra como criar o uso da coleção constituída pelo conjunto inspecionado e todas as assembléias do tempo de execução atual:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#RuntimeAssemblies)]

## <a name="create-metadataloadcontext"></a>Criar metadadosLoadContext

Para criar <xref:System.Reflection.MetadataLoadContext>o , <xref:System.Reflection.MetadataLoadContext.%23ctor%28System.Reflection.MetadataAssemblyResolver%2CSystem.String%29>invoque seu construtor <xref:System.Reflection.MetadataAssemblyResolver> , passando o previamente criado como o primeiro parâmetro e o nome de montagem do núcleo como o segundo parâmetro. Você pode omitir o nome do conjunto principal, nesse caso, o construtor tentará usar nomes padrão: "mscorlib", "System.Runtime" ou "netstandard".

Depois de criar o contexto, você pode carregar conjuntos nele <xref:System.Reflection.MetadataLoadContext.LoadFromAssemblyPath%2A>usando métodos como . Você pode usar todas as APIs de reflexão em conjuntos carregados, exceto aqueles que envolvem execução de código. O <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A> método envolve a execução de construtores, então use o <xref:System.Reflection.MemberInfo.GetCustomAttributesData%2A> método em <xref:System.Reflection.MetadataLoadContext>vez disso quando precisar examinar atributos personalizados no .

A seguinte amostra <xref:System.Reflection.MetadataLoadContext>de código cria, carrega o conjunto nele e produz atributos de montagem no console:

[!code-csharp[](snippets/inspect-contents-using-metadataloadcontext/MetadataLoadContextSnippets.cs#CreateContext)]

## <a name="example"></a>Exemplo

Para obter um exemplo de código completo, consulte [Inspecione o conteúdo do conjunto usando MetadataLoadContext](https://docs.microsoft.com/samples/dotnet/samples/inspect-assembly-contents-using-metadataloadcontext/).
