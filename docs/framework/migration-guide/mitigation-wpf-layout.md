---
title: 'Mitigação: layout de WPF'
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: 3e08a2d11e815248d0fe73f804e9ef7edb7c04da
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126108"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="cd6c7-102">Mitigação: layout de WPF</span><span class="sxs-lookup"><span data-stu-id="cd6c7-102">Mitigation: WPF Layout</span></span>
<span data-ttu-id="cd6c7-103">O layout dos controles do WPF pode ser ligeiramente alterado.</span><span class="sxs-lookup"><span data-stu-id="cd6c7-103">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="cd6c7-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="cd6c7-104">Impact</span></span>  
 <span data-ttu-id="cd6c7-105">Como resultado dessa alteração:</span><span class="sxs-lookup"><span data-stu-id="cd6c7-105">As a result of this change:</span></span>  
  
- <span data-ttu-id="cd6c7-106">A largura ou altura dos elementos pode aumentar ou reduzir em um pixel no máximo.</span><span class="sxs-lookup"><span data-stu-id="cd6c7-106">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="cd6c7-107">O posicionamento de um objeto pode ser movido até um pixel, no máximo.</span><span class="sxs-lookup"><span data-stu-id="cd6c7-107">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="cd6c7-108">Os elementos centralizados podem estar vertical ou horizontalmente fora do centro em, no máximo, um pixel.</span><span class="sxs-lookup"><span data-stu-id="cd6c7-108">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="cd6c7-109">Por padrão, esse novo layout é habilitado somente para aplicativos que se destinam ao .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="cd6c7-109">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="cd6c7-110">Redução</span><span class="sxs-lookup"><span data-stu-id="cd6c7-110">Mitigation</span></span>  
 <span data-ttu-id="cd6c7-111">Uma vez que essa modificação tende a eliminar a distorção da direita ou da parte inferior dos controles do WPF em DPIs altos, os aplicativos que de destinam a versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6, podem aderir a esse novo comportamento adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="cd6c7-111">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="cd6c7-112">Os aplicativos que se destinam ao .NET Framework 4.6, mas querem que os controles do WPF renderizem usando o algoritmo de layout anterior podem fazer isso adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="cd6c7-112">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd6c7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cd6c7-113">See also</span></span>

- [<span data-ttu-id="cd6c7-114">Alterações de redirecionamento</span><span class="sxs-lookup"><span data-stu-id="cd6c7-114">Retargeting Changes</span></span>](retargeting-changes-in-the-net-framework-4-6.md)
