---
title: Estendendo metadados por meio de atributos
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- metadata, extending
- attributes [.NET Framework], metadata
- elements [.NET Framework], attributes
- common language runtime, attributes
- annotating programming elements
- keyword-like descriptive declarations
- runtime, attributes
- extending metadata
ms.assetid: 30386922-1e00-4602-9ebf-526b271a8b87
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a31082604048e71ebc7581b36857a8bfbd333c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="extending-metadata-using-attributes"></a>Estendendo metadados por meio de atributos
O Common Language Runtime permite adicionar declarações descritivas parecidas com palavras, chamadas atributos, para anotar elementos de programação como tipos, campos, métodos e propriedades. Quando você compila seu código para o tempo de execução, ele é convertido em MSIL (Microsoft Intermediate Language) e colocado dentro de um arquivo PE (executável portátil) com metadados gerados pelo compilador. Os atributos permitem colocar informações descritivas extras em metadados que podem ser extraídos usando serviços de reflexão de tempo de execução. O compilador cria atributos quando você declara instâncias de classes especiais que derivam de <xref:System.Attribute?displayProperty=nameWithType>.  
  
 O .NET Framework usa atributos por vários motivos e para solucionar vários problemas. Os atributos descrevem como serializar dados, especificar características que são usadas para impor segurança e limitar otimizações pelo compilador JIT (Just-In-Time) para que o código permaneça fácil de depurar. Os atributos também podem registrar o nome de um arquivo ou o autor do código, ou controlar a visibilidade de controles e membros durante o desenvolvimento de formulários.  
  
## <a name="related-topics"></a>Tópicos relacionados  
  
|Título|Descrição|  
|-----------|-----------------|  
|[Aplicando atributos](../../../docs/standard/attributes/applying-attributes.md)|Descreve como aplicar um atributo a um elemento do código.|  
|[Escrevendo atributos personalizados](../../../docs/standard/attributes/writing-custom-attributes.md)|Descreve como criar classes de atributos personalizados.|  
|[Recuperando informações armazenadas em atributos](../../../docs/standard/attributes/retrieving-information-stored-in-attributes.md)|Descreve como recuperar atributos personalizados para o código que é carregado no contexto de execução.|  
|[Metadados e componentes autodescritivos](../../../docs/standard/metadata-and-self-describing-components.md)|Fornece uma visão geral dos metadados e descreve como eles são implementados em um arquivo executável PE (executável portátil) do .NET Framework.|  
|[Como carregar assemblies no contexto somente reflexão](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Explica como recuperar informações de atributos personalizados no contexto somente reflexão.|  
  
## <a name="reference"></a>Referência  
 <xref:System.Attribute?displayProperty=nameWithType>
