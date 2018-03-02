---
title: "Revisão de localização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- world-ready applications, localizability
- application development [.NET Framework], localization
- localizability [.NET Framework]
- international applications [.NET Framework], localizability
- globalization [.NET Framework], localizability
- culture, localizability
- localization [.NET Framework], localizability
- global applications, localizability
- localizing resources
ms.assetid: 3aee2fbb-de47-4e37-8fe4-ddebb9719247
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 2aaf7c466c6662611e2b37d5c967a99d050158df
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="localizability-review"></a>Revisão de localização
A revisão de localização é uma etapa intermediária no desenvolvimento de um aplicativo pronto para o mundo. Ela verifica se um aplicativo globalizado está pronto para a localização e identifica qualquer código ou aspecto da interface do usuário que exija tratamento especial. Esta etapa também ajuda a garantir que o processo de localização não apresente qualquer defeito funcionais em seu aplicativo. Quando todos os problemas levantados pela revisão de localização forem resolvidos, o aplicativo estará pronto para a localização. Se a revisão de localização estiver concluída, você não precisará modificar qualquer código-fonte durante o processo de localização.  
  
 A revisão de localização é composta pelas três verificações a seguir:  
  
-   [As recomendações de globalização foram implementadas?](#global)  
  
-   [Os recursos sensíveis à cultura foram tratados corretamente?](#culture)  
  
-   [Você testou seu aplicativo com dados internacionais?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Implementando recomendações de globalização  
 Se você tiver projetado e desenvolvido seu aplicativo com a localização em mente, e se tiver seguido as recomendações discutidas no artigo [Globalização](../../../docs/standard/globalization-localization/globalization.md), a revisão de localização será essencialmente uma aprovação da garantia de qualidade. Caso contrário, durante esse estágio, examine e implemente as recomendações para [globalização](../../../docs/standard/globalization-localization/globalization.md) e corrija os erros no código-fonte que impedem a localização.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Tratando Recursos Sensíveis à Cultura  
 O .NET Framework não dá suporte de programação em várias áreas que podem variar amplamente com a cultura. Na maioria dos casos, você deve escrever um código personalizado para lidar com áreas de recurso como as seguintes:  
  
-   Endereços.  
  
-   Números de telefone.  
  
-   Tamanhos de papel.  
  
-   Unidades de medida usadas para comprimentos, pesos, área, volume e temperaturas. Embora o .NET Framework não ofereça suporte interno para conversão de unidades de medida, você pode usar a propriedade <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> para determinar se um certo país ou região usa o sistema métrico, como mostra o exemplo a seguir.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Testando o aplicativo  
 Antes de localizar seu aplicativo, você deve testá-lo usando dados internacionais em versões internacionais do sistema operacional. Apesar de grande parte da interface do usuário não estar localizada neste ponto, você será capaz de detectar problemas, como os seguintes:  
  
-   Os dados serializados que não desserializam corretamente entre as versões do sistema operacional.  
  
-   Os dados numéricos que não refletem as convenções da cultura atual. Por exemplo, os números poderão ser exibidos com separadores de grupo imprecisos, separadores decimais ou símbolos de moeda.  
  
-   Dados de data e hora que não refletem as convenções da cultura atual. Por exemplo, números que representam o mês e o dia podem aparecer na ordem errada, separadores de data podem estar incorretos ou informações de fuso horário podem estar incorretas.  
  
-   Os recursos que não podem ser encontrados porque você não identificou uma cultura padrão para o seu aplicativo.  
  
-   As cadeias de caracteres que são exibidas em uma ordem incomum para a cultura específica.  
  
-   As comparações de cadeia de caracteres ou comparações de igualdade que retornam resultados inesperados.  
  
 Se você tiver seguido as recomendações de globalização ao desenvolver seu aplicativo, sendo tratadas corretamente, tratado os recursos sensíveis à cultura e identificado e resolvido os problemas de localização que surgiram durante o teste, você poderá prosseguir para a próxima etapa, [Localização](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Globalização e localização](../../../docs/standard/globalization-localization/index.md)  
 [Localização](../../../docs/standard/globalization-localization/localization.md)  
 [Globalização](../../../docs/standard/globalization-localization/globalization.md)  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
