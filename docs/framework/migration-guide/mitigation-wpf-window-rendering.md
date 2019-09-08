---
title: 'Mitigação: Renderização de janela WPF'
ms.date: 03/30/2017
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13091c06561da24d2fc03f810fd8b8687b21d9a4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70789795"
---
# <a name="mitigation-wpf-window-rendering"></a><span data-ttu-id="bdf9b-102">Mitigação: Renderização de janela WPF</span><span class="sxs-lookup"><span data-stu-id="bdf9b-102">Mitigation: WPF Window Rendering</span></span>

<span data-ttu-id="bdf9b-103">No .NET Framework 4.6 em execução no Windows 8 e superior, a janela inteira é renderizada sem distorção quando ela se estende para fora da exibição única em um cenário de vários monitores.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span>

## <a name="impact"></a><span data-ttu-id="bdf9b-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="bdf9b-104">Impact</span></span>

<span data-ttu-id="bdf9b-105">Em geral, a renderização de uma janela inteira em vários monitores sem distorção é o comportamento esperado.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-105">In general, rendering an entire window across multiple monitors without clipping is the expected behavior.</span></span> <span data-ttu-id="bdf9b-106">No entanto, no Windows 7 e versões anteriores, as janelas do WPF são cortadas quando elas ultrapassam uma exibição única, pois renderizar uma parte da janela no segundo monitor tem um impacto significativo de desempenho.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-106">However, on Windows 7 and earlier versions, WPF windows are clipped when they extend beyond a single display because rendering a portion of the window on the second monitor has a significant performance impact.</span></span>

<span data-ttu-id="bdf9b-107">O impacto preciso da renderização das janelas do WPF em monitores no Windows 8 e superior não é precisamente quantificável, pois depende de um grande número de fatores.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-107">The precise impact of rendering WPF windows across monitors on Windows 8 and above is not precisely quantifiable since it depends on a large number of factors.</span></span> <span data-ttu-id="bdf9b-108">Em alguns casos, ele ainda pode produzir um impacto indesejável no desempenho, especialmente para os usuários que executam aplicativos de uso intensivo de gráficos e que têm janelas que transpõem monitores.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-108">In some cases, it may still produce an undesirable impact on performance, particularly for users who run graphics-intensive applications and have windows straddling monitors.</span></span> <span data-ttu-id="bdf9b-109">Em outros casos, você pode simplesmente querer um comportamento consistente nas versões do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-109">In other cases, you may simply want a consistent behavior across .NET Framework versions.</span></span>

## <a name="mitigation"></a><span data-ttu-id="bdf9b-110">Redução</span><span class="sxs-lookup"><span data-stu-id="bdf9b-110">Mitigation</span></span>

<span data-ttu-id="bdf9b-111">Você pode desabilitar essa alteração e reverter para o comportamento anterior de distorção de uma janela do WPF quando ela ultrapassa uma exibição única.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-111">You can disable this change and revert to the previous behavior of clipping a WPF window when it extends beyond a single display.</span></span> <span data-ttu-id="bdf9b-112">Há duas formas de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="bdf9b-112">There are two ways to do this:</span></span>

- <span data-ttu-id="bdf9b-113">Ao adicionar o elemento `<EnableMultiMonitorDisplayClipping>` à seção `<appSettings>` do seu arquivo de configuração de aplicativo, você pode desabilitar ou habilitar esse comportamento em aplicativos que são executados no Windows 8 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-113">By adding the `<EnableMultiMonitorDisplayClipping>` element to the `<appSettings>` section of your application configuration file, you can disable or enable this behavior on apps running on Windows 8 or later.</span></span> <span data-ttu-id="bdf9b-114">Por exemplo, a seguinte seção de configuração desabilita a renderização sem distorção:</span><span class="sxs-lookup"><span data-stu-id="bdf9b-114">For example, the following configuration section disables rendering without clipping:</span></span>

  ```xml
  <appSettings>
      <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    </appSettings>
  ```

  <span data-ttu-id="bdf9b-115">A definição de configuração do `<EnableMultiMonitorDisplayClipping>` pode ter um dos dois valores:</span><span class="sxs-lookup"><span data-stu-id="bdf9b-115">The `<EnableMultiMonitorDisplayClipping>` configuration setting can have either of two values:</span></span>

  - <span data-ttu-id="bdf9b-116">`true`, para habilitar a distorção das janelas e monitorar limites durante a renderização.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-116">`true`, to enable clipping of windows to monitor bounds during rendering.</span></span>

  - <span data-ttu-id="bdf9b-117">`false`, para desabilitar a distorção das janelas e monitorar limites durante a renderização.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-117">`false`, to disable clipping of windows to monitor bounds during rendering.</span></span>

- <span data-ttu-id="bdf9b-118">Definindo a propriedade <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> como `true` na inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bdf9b-118">By setting the <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> property to `true` at app startup.</span></span>

## <a name="see-also"></a><span data-ttu-id="bdf9b-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdf9b-119">See also</span></span>

- [<span data-ttu-id="bdf9b-120">Alterações no tempo de execução</span><span class="sxs-lookup"><span data-stu-id="bdf9b-120">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
