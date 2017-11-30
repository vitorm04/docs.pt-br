---
title: "Localização"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a>Localização
A localização é o processo de converter os recursos do aplicativo em versões localizadas para cada cultura que o aplicativo oferecerá suporte. Você deve prosseguir para a etapa de localização somente após concluir o [revisão de localização](../../../docs/standard/globalization-localization/localizability-review.md) etapa para verificar se o aplicativo globalizado está pronto para a localização.  
  
 Um aplicativo que está pronto para a localização é separado em dois blocos conceituais, um bloco que contém todos os elementos de interface de usuário e um bloco que contém o código executável. O bloco de interface do usuário contém apenas os elementos de interface de usuário localizáveis, como cadeias de caracteres, mensagens de erro, caixas de diálogo, menus, recursos do objeto inserido, e assim por diante para a cultura neutra. O bloco de código contém apenas o código do aplicativo a ser usado por todas as culturas com suporte. O common language runtime oferece suporte a um modelo de recurso de assembly satélite que separa o código executável do aplicativo de seus recursos. Para obter mais informações sobre como implementar esse modelo, consulte [recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md).  
  
 Para cada versão localizada do seu aplicativo, adicione um novo assembly satélite que contém o bloco de interface do usuário localizada traduzido para o idioma apropriado para a cultura de destino. O bloco de código para todas as culturas deve permanecer o mesmo. A combinação de uma versão localizada do bloco de interface de usuário com o bloco de código produz uma versão localizada do seu aplicativo.  
  
 O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fornece um Editor de recursos do Windows Forms (Winres.exe) que permite que você localize rapidamente formulários do Windows para culturas de destino. Para obter informações sobre como usar essa ferramenta, consulte [Winres.exe (Editor de recursos do Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## <a name="see-also"></a>Consulte também  
 [Globalização e localização](../../../docs/standard/globalization-localization/index.md)  
 [Análise de possibilidade de localização](../../../docs/standard/globalization-localization/localizability-review.md)  
 [Globalização](../../../docs/standard/globalization-localization/globalization.md)  
 [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
