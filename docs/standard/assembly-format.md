---
title: Formato de arquivo do Assembly .NET
description: "Saiba mais sobre o formato de arquivo do assembly do .NET, que é usado para descrever e conter aplicativos e bibliotecas do .NET."
keywords: .NET, .NET Core
author: richlander
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 6520323e-ff28-4c8a-ba80-e64a413199e6
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d219a584f2f5521fc3b0fd00ab037a8e486c9050
ms.sourcegitcommit: 75a180acb5d8a2dbd4a52915ce8e980749fb1d05
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/24/2018
---
# <a name="net-assembly-file-format"></a>Formato de arquivo do Assembly .NET

O .NET define um formato de arquivo binário – "assembly" – que é usado para descrever completamente e conter programas .NET. Os assemblies são usados para os programas em si, bem como todas as bibliotecas dependentes. Um programa .NET pode ser executado como um ou mais assemblies, sem a necessidade de nenhum outro artefato, além da implementação do .NET apropriado. As dependências nativas, incluindo APIs do sistema operacional, são uma preocupação separada e não estão contidas no formato de assembly do .NET, embora, às vezes, sejam descritas com esse formato (por exemplo, WinRT).

> Cada componente de CLI carrega os metadados para declarações, implementações e referências específicas para esse componente. Portanto, os metadados específicos do componente são conhecidos como metadados de componente e o componente resultante deve ser autodescritivo – do ECMA 335 I.9.1, Componentes e assemblies.

O formato é totalmente especificado e padronizado como [ECMA 335](http://www.ecma-international.org/publications/standards/Ecma-335.htm). Todos os tempos de execução e compiladores .NET usam esse formato. A presença de um formato binário documentado e atualizado raramente foi uma grande vantagem (sem dúvida, um requisito) da interoperabilidade. O formato foi atualizado de forma substancial pela última vez em 2005 (.NET 2.0) para acomodar os genéricos e a arquitetura do processador.

O formato é independente de CPU e sistema operacional. Ele tem sido usado como parte de implementações do .NET que se destinam a muitos chips e CPUs. Embora o formato em si tenha patrimônio do Windows, é implementável em qualquer sistema operacional. Sua escolha indiscutivelmente mais significativa para a interoperabilidade do sistema operacional é que a maioria dos valores é armazenada no formato little endian. Ele não tem uma afinidade específica para o tamanho do ponteiro de computador (por exemplo, 32 bits, 64 bits).

O formato do assembly .NET também é muito descritivo sobre a estrutura de um determinado programa ou biblioteca. Ele descreve os componentes internos de um assembly, especificamente: referências de assembly e tipos definidos e suas estruturas internas. APIs ou ferramentas podem ler e processar essas informações para exibição ou para tomar decisões de programação.

## <a name="format"></a>Formatar

O formato binário do .NET se baseia no formato de [arquivo PE](http://en.wikipedia.org/wiki/Portable_Executable) do Windows. Na verdade, as bibliotecas de classes do .NET são compatíveis com PEs do Windows e, a primeira vista, parecem ser DLLs (bibliotecas de vínculo dinâmico) do Windows ou EXEs (executáveis) de aplicativo. Essa é uma característica muito útil no Windows, no qual elas podem se mascarar como binários executáveis nativos e obter parte do mesmo tratamento (por exemplo, o carregamento do sistema operacional, ferramentas PE).

![Cabeçalhos de assembly](./media/assembly-format/assembly-headers.png)

Cabeçalhos de assembly do ECMA 335 II.25.1, Estrutura do formato de arquivo do tempo de execução.

## <a name="processing-the-assemblies"></a>Processando os assemblies

É possível escrever APIs ou ferramentas para processar assemblies. As informações do assembly permitem tomar decisões de programação no tempo de execução, reescrever os assemblies, fornecer o IntelliSense de API em um editor e gerar a documentação. <xref:System.Reflection?displayProperty=nameWithType> e [Mono.Cecil](http://www.mono-project.com/docs/tools+libraries/libraries/Mono.Cecil/) são bons exemplos de ferramentas que frequentemente são usadas para essa finalidade.
