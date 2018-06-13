---
title: 'Os analisadores do Roslyn: .NET'
description: Saiba mais sobre os analisadores do Roslyn que localizam problemas e sugerem correções.
author: billwagner
ms.author: billwagner
ms.date: 01/24/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ec153b8fed08ef245a3a0f58970b4e3955dfacb5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33567257"
---
# <a name="the-roslyn-based-analyzers"></a>Os analisadores do Roslyn

Os analisadores do Roslyn usam o .NET Compiler SDK (APIs do Roslyn) para analisar o código-fonte do seu projeto para localizar problemas e sugerir correções. Analisadores diferentes procuram diferentes classes de problemas, variando de práticas que podem causar erros a problemas de segurança à compatibilidade da API.

Os analisadores do Roslyn trabalham tanto interativamente quanto durante as compilações. O analisador fornece uma orientações diferentes no Visual Studio ou em compilações da linha de comando.

Embora você edite códigos no Visual Studio, os analisadores são executados enquanto você faz alterações, capturando possíveis problemas assim que você cria um código que aciona problemas. Os problemas são destacados com linhas onduladas abaixo deles. O Visual Studio exibe uma lâmpada. Quando você clica nela, o analisador sugere soluções possíveis para o problema. Quando você compila o projeto, no Visual Studio ou na linha de comando, o código-fonte é analisado, e o analisador fornece uma lista completa de possíveis problemas. A imagem a seguir mostra um exemplo.

![problemas relatados pelo analisador de estrutura](./media/framework-analyzers-2.png)

Os analisadores do Roslyn relatam problemas potenciais como erros, avisos ou informações com base na gravidade do problema.

É possível instalar os analisadores do Roslyn como pacotes NuGet no projeto. Os analisadores configurados e qualquer configuração para cada analisador são restaurados e executados no computador de qualquer desenvolvedor para o projeto.

> [!NOTE]
> A experiência do usuário com os analisadores do Roslyn é diferente da experiência com as bibliotecas de análise de código, como as versões mais antigas do FxCop e as ferramentas de análise de segurança.  Você não precisa executar explicitamente os analisadores do Roslyn. Não é necessário usar os itens de menu "Executar análise de código" no menu "Analisar" do Visual Studio. Os analisadores do Roslyn executam de forma assíncrona enquanto você trabalha. 

## <a name="more-information-on-specific-analyzers"></a>Mais informações sobre analisadores específicos

Os analisadores a seguir são abordados nesta seção:

[Analisador de API](api-analyzer.md): este analisador verifica se há em seu código possíveis riscos de compatibilidade ou usos de APIs obsoletas.    
[Analisador de estrutura](framework-analyzer.md): este analisador examina seu código para garantir que ele segue as diretrizes dos aplicativos do .NET Framework. Essas regras incluem várias recomendações com base em segurança.
