---
title: 'Mitigação: layout de WPF'
description: Saiba como atenuar os problemas resultantes de uma alteração no layout de controles do WPF, como o posicionamento de um objeto que se move em um pixel.
ms.date: 03/30/2017
ms.assetid: 805ffd7f-8d1e-427e-a648-601ca8ec37a5
ms.openlocfilehash: e4e4612f7b39eefbf0e76ac86c8eb644c257ba75
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475340"
---
# <a name="mitigation-wpf-layout"></a><span data-ttu-id="5dc55-103">Mitigação: layout de WPF</span><span class="sxs-lookup"><span data-stu-id="5dc55-103">Mitigation: WPF Layout</span></span>
<span data-ttu-id="5dc55-104">O layout dos controles do WPF pode ser ligeiramente alterado.</span><span class="sxs-lookup"><span data-stu-id="5dc55-104">The layout of WPF controls can change slightly.</span></span>  
  
## <a name="impact"></a><span data-ttu-id="5dc55-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="5dc55-105">Impact</span></span>  
 <span data-ttu-id="5dc55-106">Como resultado dessa alteração:</span><span class="sxs-lookup"><span data-stu-id="5dc55-106">As a result of this change:</span></span>  
  
- <span data-ttu-id="5dc55-107">A largura ou altura dos elementos pode aumentar ou reduzir em um pixel no máximo.</span><span class="sxs-lookup"><span data-stu-id="5dc55-107">The width or height of elements may grow or shrink by at most one pixel.</span></span>  
  
- <span data-ttu-id="5dc55-108">O posicionamento de um objeto pode ser movido até um pixel, no máximo.</span><span class="sxs-lookup"><span data-stu-id="5dc55-108">The placement of an object can move by at most one pixel.</span></span>  
  
- <span data-ttu-id="5dc55-109">Os elementos centralizados podem estar vertical ou horizontalmente fora do centro em, no máximo, um pixel.</span><span class="sxs-lookup"><span data-stu-id="5dc55-109">Centered elements can be vertically or horizontally off center by at most one pixel.</span></span>  
  
 <span data-ttu-id="5dc55-110">Por padrão, esse novo layout é habilitado somente para aplicativos que se destinam ao .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="5dc55-110">By default, this new layout is enabled only for apps that target the .NET Framework 4.6.</span></span>  
  
## <a name="mitigation"></a><span data-ttu-id="5dc55-111">Atenuação</span><span class="sxs-lookup"><span data-stu-id="5dc55-111">Mitigation</span></span>  
 <span data-ttu-id="5dc55-112">Uma vez que essa modificação tende a eliminar a distorção da direita ou da parte inferior dos controles do WPF em DPIs altos, os aplicativos que de destinam a versões anteriores do .NET Framework, mas estão sendo executados no .NET Framework 4.6, podem aderir a esse novo comportamento adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="5dc55-112">Since this modification tends to eliminate clipping of the right or bottom of WPF controls at high DPIs, apps that target earlier versions of the .NET Framework but are running on the .NET Framework 4.6 can opt into this new behavior by adding the following line to the `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false" />  
```  
  
 <span data-ttu-id="5dc55-113">Os aplicativos que se destinam ao .NET Framework 4.6, mas querem que os controles do WPF renderizem usando o algoritmo de layout anterior podem fazer isso adicionando a seguinte linha à seção `<runtime>` do arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="5dc55-113">Apps that target the .NET Framework 4.6 but want WPF controls to render using the previous layout algorithm can do so by adding the following line to the  `<runtime>` section of the app.config file:</span></span>  
  
```xml  
<AppContextSwitchOverrides value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="5dc55-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5dc55-114">See also</span></span>

- [<span data-ttu-id="5dc55-115">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="5dc55-115">Application compatibility</span></span>](application-compatibility.md)
