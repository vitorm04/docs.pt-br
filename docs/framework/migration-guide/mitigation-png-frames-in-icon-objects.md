---
title: 'Mitigação: Quadros PNG em objetos de ícone'
ms.date: 03/30/2017
ms.assetid: ca87fefb-7144-4b4e-8832-5a939adbb4b2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d67b2fac0c1d55bfa5594e90998d9613de4ad271
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659781"
---
# <a name="mitigation-png-frames-in-icon-objects"></a><span data-ttu-id="edd76-102">Mitigação: Quadros PNG em objetos de ícone</span><span class="sxs-lookup"><span data-stu-id="edd76-102">Mitigation: PNG Frames in Icon Objects</span></span>
<span data-ttu-id="edd76-103">A partir do .NET Framework 4.6, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> converte com êxito ícones com quadros PNG em objetos <xref:System.Drawing.Bitmap>.</span><span class="sxs-lookup"><span data-stu-id="edd76-103">Starting with the .NET Framework 4.6, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method successfully converts icons with PNG frames into <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="edd76-104">Em aplicativos direcionados ao .NET Framework 4.5.2 e versões anteriores, o método <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> gera uma exceção <xref:System.ArgumentOutOfRangeException> quando o objeto <xref:System.Drawing.Icon> tem quadros PNG.</span><span class="sxs-lookup"><span data-stu-id="edd76-104">In apps that target the .NET Framework 4.5.2 and earlier versions, the <xref:System.Drawing.Icon.ToBitmap%2A?displayProperty=nameWithType> method throws an <xref:System.ArgumentOutOfRangeException> exception if the <xref:System.Drawing.Icon> object has PNG frames.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="edd76-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="edd76-105">Impact</span></span>  
 <span data-ttu-id="edd76-106">Essa alteração afeta aplicativos que são recompilados para direcionamento ao .NET Framework 4.6 e que implementam tratamento especial para a <xref:System.ArgumentOutOfRangeException> que será gerada se um objeto <xref:System.Drawing.Icon> tiver quadros PNG.</span><span class="sxs-lookup"><span data-stu-id="edd76-106">This change affects apps that are recompiled to target the .NET Framework 4.6 and that implement special handling for the <xref:System.ArgumentOutOfRangeException> that is thrown when an <xref:System.Drawing.Icon> object has PNG frames.</span></span> <span data-ttu-id="edd76-107">Ao executar no .NET Framework 4.6, a conversão é bem-sucedida, uma <xref:System.ArgumentOutOfRangeException> não é mais gerada e, portanto, o manipulador de exceção não é invocado.</span><span class="sxs-lookup"><span data-stu-id="edd76-107">When running under the .NET Framework 4.6, the conversion is successful, an <xref:System.ArgumentOutOfRangeException> is no longer thrown, and therefore the exception handler is no longer invoked.</span></span>  
  
### <a name="mitigation"></a><span data-ttu-id="edd76-108">Redução</span><span class="sxs-lookup"><span data-stu-id="edd76-108">Mitigation</span></span>  
 <span data-ttu-id="edd76-109">Se esse comportamento for indesejável, será possível reter o comportamento anterior adicionando o seguinte elemento à seção [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="edd76-109">If this behavior is undesirable, you can retain the previous behavior by adding the following element to the [\<runtime>](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) section of your app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true" />  
```  
  
 <span data-ttu-id="edd76-110">Se o arquivo app.config já contiver o elemento `AppContextSwitchOverrides`, o novo valor deverá ser mesclado ao atributo `value`, da seguinte forma:</span><span class="sxs-lookup"><span data-stu-id="edd76-110">If the app.config file already contains the `AppContextSwitchOverrides` element, the new value should be merged with the `value` attribute like this:</span></span>  
  
```xml  
<AppContextSwitchOverrides   
      value="Switch.System.Drawing.DontSupportPngFramesInIcons=true;<previous key>=<previous value>" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="edd76-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edd76-111">See also</span></span>
- [<span data-ttu-id="edd76-112">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="edd76-112">Retargeting Changes</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-6.md)
