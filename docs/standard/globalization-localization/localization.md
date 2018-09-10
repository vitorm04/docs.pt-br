---
title: Localização
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee7de15130644e63b17a6d067c5cce9088d199a0
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44185042"
---
# <a name="localization"></a>Localização
Localização é o processo de traduzir os recursos do aplicativo em versões localizadas para cada cultura à qual o aplicativo dará suporte. Você deve prosseguir para a etapa de localização somente após concluir a etapa de [Revisão de Capacidade de Localização](../../../docs/standard/globalization-localization/localizability-review.md) para verificar se o aplicativo globalizado está pronto para a localização.  
  
 Um aplicativo que está pronto para a localização é separado em dois blocos conceituais: um bloco que contém todos os elementos de interface de usuário e um bloco que contém o código executável. O bloco de interface do usuário contém apenas os elementos de interface de usuário localizáveis, como cadeias de caracteres, mensagens de erro, caixas de diálogo, menus, recursos de objetos inseridos e assim por diante para a cultura neutra. O bloco de código contém apenas o código do aplicativo a ser usado por todas as culturas com suporte. O common language runtime dá suporte a um modelo de recurso de assembly satélite que separa o código executável do aplicativo de seus recursos. Para saber mais sobre como implementar esse modelo, confira [Recursos em aplicativos da área de trabalho](../../../docs/framework/resources/index.md).  
  
 Para cada versão localizada do aplicativo, adicione um novo assembly satélite que contenha o bloco de interface do usuário localizada traduzido para o idioma apropriado para a cultura de destino. O bloco de código para todas as culturas deve permanecer o mesmo. A combinação de uma versão localizada do bloco de interface de usuário com o bloco de código produz uma versão localizada do aplicativo.  
  
 O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fornece o Windows Forms Resource Editor (Winres.exe), que permite que você localize rapidamente Windows Forms para culturas de destino. Para saber mais sobre como usar essa ferramenta, confira [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## <a name="see-also"></a>Consulte também

- [Globalização e localização](../../../docs/standard/globalization-localization/index.md)  
- [Análise de possibilidade de localização](../../../docs/standard/globalization-localization/localizability-review.md)  
- [Globalização](../../../docs/standard/globalization-localization/globalization.md)  
- [Recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md)
