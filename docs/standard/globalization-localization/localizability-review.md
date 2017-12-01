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
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7633c7fe9e99bde96ee108460e983eff48f1c7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="localizability-review"></a>Revisão de localização
A revisão de localização é uma etapa intermediária no desenvolvimento de um aplicativo preparado para o mundo. Ele verifica se um aplicativo globalizado está pronto para a localização e identifica qualquer código ou qualquer aspectos da interface do usuário que requerem tratamento especial. Esta etapa também ajuda a garantir que o processo de localização não apresentará qualquer funcionais defeitos em seu aplicativo. Quando todos os problemas gerados pela revisão de localização foram resolvidos, o aplicativo está pronto para localização. Se a revisão de localização estiver completa, você não deve ter que modificar qualquer código de origem durante o processo de localização.  
  
 A revisão de localização consiste as seguintes verificações de três:  
  
-   [As recomendações de globalização são implementadas?](#global)  
  
-   [Recursos de cultura são tratados corretamente?](#culture)  
  
-   [Teste seu aplicativo com dados internacionais?](#test)  
  
<a name="global"></a>   
## <a name="implementing-globalization-recommendations"></a>Implementando recomendações de globalização  
 Se você tiver criado e desenvolvido seu aplicativo com a localização em mente e se você tiver seguido as recomendações discutido no [globalização](../../../docs/standard/globalization-localization/globalization.md) artigo, a revisão de localização será amplamente uma passagem de garantia de qualidade . Caso contrário, durante esse estágio Examine e implementar as recomendações para [globalização](../../../docs/standard/globalization-localization/globalization.md)e corrija os erros que impedem a localização no código-fonte.  
  
<a name="culture"></a>   
## <a name="handling-culture-sensitive-features"></a>Tratando Recursos Sensíveis à Cultura  
 O .NET Framework não dá suporte em um número de áreas que podem variar amplamente pela cultura. Na maioria dos casos, você deve escrever código personalizado para lidar com áreas de recurso com o seguinte:  
  
-   Endereços.  
  
-   Números de telefone.  
  
-   Tamanhos de papel.  
  
-   Unidades de medida usado para comprimentos, pesos, área, volume e temperaturas. Embora o .NET Framework não oferece suporte interno para converter entre unidades de medida, você pode usar o <xref:System.Globalization.RegionInfo.IsMetric%2A?displayProperty=nameWithType> para determinar se um determinado país ou região usa o sistema métrico, como mostra o exemplo a seguir.  
  
     [!code-csharp[Conceptual.Localizability#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.localizability/cs/ismetric1.cs#1)]
     [!code-vb[Conceptual.Localizability#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.localizability/vb/ismetric1.vb#1)]  
  
<a name="test"></a>   
## <a name="testing-your-application"></a>Testando o aplicativo  
 Antes de você localiza o aplicativo, você deve testá-lo usando dados internacionais em versões internacionais do sistema operacional. Embora a maioria da interface do usuário não será localizada neste ponto, você será capaz de detectar problemas, como o seguinte:  
  
-   Dados serializados não desserializar corretamente nas versões do sistema operacional.  
  
-   Dados numéricos que não refletem as convenções da cultura atual. Por exemplo, os números poderão ser exibidos com separadores de grupo precisas, separadores decimais ou símbolos de moeda.  
  
-   Dados de data e hora que não refletem as convenções da cultura atual. Por exemplo, números que representam o mês e dia podem aparecer na ordem errada, separadores de data podem estar incorretos ou informações de fuso horário podem estar incorretas.  
  
-   Recursos que não podem ser encontrados porque não identificou uma cultura padrão para seu aplicativo.  
  
-   Cadeias de caracteres que são exibidas em uma ordem incomum para a cultura específica.  
  
-   Comparações de igualdade que retornam resultados inesperados ou de comparações de cadeia de caracteres.  
  
 Se você tiver seguido as recomendações de globalização ao desenvolver seu aplicativo, sendo tratadas corretamente, os recursos de cultura e identificados e resolvidos os problemas de localização que ocorreu durante o teste, você pode prosseguir para a próxima etapa, [Localização](../../../docs/standard/globalization-localization/localization.md).  
  
## <a name="see-also"></a>Consulte também  
 [Globalização e localização](../../../docs/standard/globalization-localization/index.md)  
 [Localização](../../../docs/standard/globalization-localization/localization.md)  
 [Globalização](../../../docs/standard/globalization-localization/globalization.md)  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
