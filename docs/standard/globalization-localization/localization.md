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
# <a name="localization"></a><span data-ttu-id="92d49-102">Localização</span><span class="sxs-lookup"><span data-stu-id="92d49-102">Localization</span></span>
<span data-ttu-id="92d49-103">A localização é o processo de converter os recursos do aplicativo em versões localizadas para cada cultura que o aplicativo oferecerá suporte.</span><span class="sxs-lookup"><span data-stu-id="92d49-103">Localization is the process of translating an application's resources into localized versions for each culture that the application will support.</span></span> <span data-ttu-id="92d49-104">Você deve prosseguir para a etapa de localização somente após concluir o [revisão de localização](../../../docs/standard/globalization-localization/localizability-review.md) etapa para verificar se o aplicativo globalizado está pronto para a localização.</span><span class="sxs-lookup"><span data-stu-id="92d49-104">You should proceed to the localization step only after completing the [Localizability Review](../../../docs/standard/globalization-localization/localizability-review.md) step to verify that the globalized application is ready for localization.</span></span>  
  
 <span data-ttu-id="92d49-105">Um aplicativo que está pronto para a localização é separado em dois blocos conceituais, um bloco que contém todos os elementos de interface de usuário e um bloco que contém o código executável.</span><span class="sxs-lookup"><span data-stu-id="92d49-105">An application that is ready for localization is separated into two conceptual blocks, a block that contains all user interface elements and a block that contains executable code.</span></span> <span data-ttu-id="92d49-106">O bloco de interface do usuário contém apenas os elementos de interface de usuário localizáveis, como cadeias de caracteres, mensagens de erro, caixas de diálogo, menus, recursos do objeto inserido, e assim por diante para a cultura neutra.</span><span class="sxs-lookup"><span data-stu-id="92d49-106">The user interface block contains only localizable user-interface elements such as strings, error messages, dialog boxes, menus, embedded object resources, and so on for the neutral culture.</span></span> <span data-ttu-id="92d49-107">O bloco de código contém apenas o código do aplicativo a ser usado por todas as culturas com suporte.</span><span class="sxs-lookup"><span data-stu-id="92d49-107">The code block contains only the application code to be used by all supported cultures.</span></span> <span data-ttu-id="92d49-108">O common language runtime oferece suporte a um modelo de recurso de assembly satélite que separa o código executável do aplicativo de seus recursos.</span><span class="sxs-lookup"><span data-stu-id="92d49-108">The common language runtime supports a satellite assembly resource model that separates an application's executable code from its resources.</span></span> <span data-ttu-id="92d49-109">Para obter mais informações sobre como implementar esse modelo, consulte [recursos em aplicativos de área de trabalho](../../../docs/framework/resources/index.md).</span><span class="sxs-lookup"><span data-stu-id="92d49-109">For more information about implementing this model, see [Resources in Desktop Apps](../../../docs/framework/resources/index.md).</span></span>  
  
 <span data-ttu-id="92d49-110">Para cada versão localizada do seu aplicativo, adicione um novo assembly satélite que contém o bloco de interface do usuário localizada traduzido para o idioma apropriado para a cultura de destino.</span><span class="sxs-lookup"><span data-stu-id="92d49-110">For each localized version of your application, add a new satellite assembly that contains the localized user interface block translated into the appropriate language for the target culture.</span></span> <span data-ttu-id="92d49-111">O bloco de código para todas as culturas deve permanecer o mesmo.</span><span class="sxs-lookup"><span data-stu-id="92d49-111">The code block for all cultures should remain the same.</span></span> <span data-ttu-id="92d49-112">A combinação de uma versão localizada do bloco de interface de usuário com o bloco de código produz uma versão localizada do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92d49-112">The combination of a localized version of the user interface block with the code block produces a localized version of your application.</span></span>  
  
 <span data-ttu-id="92d49-113">O [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fornece um Editor de recursos do Windows Forms (Winres.exe) que permite que você localize rapidamente formulários do Windows para culturas de destino.</span><span class="sxs-lookup"><span data-stu-id="92d49-113">The [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] supplies the Windows Forms Resource Editor (Winres.exe) that allows you to quickly localize Windows Forms for target cultures.</span></span> <span data-ttu-id="92d49-114">Para obter informações sobre como usar essa ferramenta, consulte [Winres.exe (Editor de recursos do Windows Forms)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span><span class="sxs-lookup"><span data-stu-id="92d49-114">For information about using this tool, see [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d49-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92d49-115">See Also</span></span>  
 [<span data-ttu-id="92d49-116">Globalização e localização</span><span class="sxs-lookup"><span data-stu-id="92d49-116">Globalization and Localization</span></span>](../../../docs/standard/globalization-localization/index.md)  
 [<span data-ttu-id="92d49-117">Análise de possibilidade de localização</span><span class="sxs-lookup"><span data-stu-id="92d49-117">Localizability Review</span></span>](../../../docs/standard/globalization-localization/localizability-review.md)  
 [<span data-ttu-id="92d49-118">Globalização</span><span class="sxs-lookup"><span data-stu-id="92d49-118">Globalization</span></span>](../../../docs/standard/globalization-localization/globalization.md)  
 [<span data-ttu-id="92d49-119">Recursos em aplicativos de área de trabalho</span><span class="sxs-lookup"><span data-stu-id="92d49-119">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
