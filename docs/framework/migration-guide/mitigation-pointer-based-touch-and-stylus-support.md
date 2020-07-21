---
title: 'Mitigação: suporte a toque e caneta com base em ponteiro'
description: Saiba mais sobre os efeitos de habilitar uma pilha opcional do WPF Touch/Stylus para aplicativos do WPF direcionados .NET Framework 4,7.
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: d0c0effeaa727c615dddc3b92cdd34aafde65705
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475418"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="d3945-103">Mitigação: suporte a toque e caneta com base em ponteiro</span><span class="sxs-lookup"><span data-stu-id="d3945-103">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="d3945-104">Os aplicativos do WPF destinados ao .NET Framework 4,7 e que estão em execução no Windows a partir da atualização do Windows 10 para criadores podem permitir uma `WM_POINTER` pilha de toque/caneta do WPF baseada em opcionais.</span><span class="sxs-lookup"><span data-stu-id="d3945-104">WPF applications that target the .NET Framework 4.7 and are running on Windows starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="d3945-105">Impacto</span><span class="sxs-lookup"><span data-stu-id="d3945-105">Impact</span></span>

<span data-ttu-id="d3945-106">Os desenvolvedores que não habilitarem explicitamente o suporte a toque/caneta com base em ponteiro não verão nenhuma alteração no comportamento de toque/caneta do WPF.</span><span class="sxs-lookup"><span data-stu-id="d3945-106">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="d3945-107">A seguir estão os problemas conhecidos no momento com a pilha de toque/caneta com base em `WM_POINTER` opcional:</span><span class="sxs-lookup"><span data-stu-id="d3945-107">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="d3945-108">Não há suporte para escrita à tinta em tempo real.</span><span class="sxs-lookup"><span data-stu-id="d3945-108">No support for real-time inking.</span></span>

   <span data-ttu-id="d3945-109">Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles são processados no thread da interface do usuário, o que pode levar a um desempenho ruim.</span><span class="sxs-lookup"><span data-stu-id="d3945-109">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="d3945-110">Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="d3945-110">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="d3945-111">A manipulação pode se comportar de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="d3945-111">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="d3945-112">Arrastar/soltar não mostrará comentários apropriados para entrada por toque.</span><span class="sxs-lookup"><span data-stu-id="d3945-112">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="d3945-113">(Isso não afeta entrada de caneta).</span><span class="sxs-lookup"><span data-stu-id="d3945-113">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="d3945-114">Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta.</span><span class="sxs-lookup"><span data-stu-id="d3945-114">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="d3945-115">Isso pode fazer com que o aplicativo pare de responder até que a entrada do mouse seja detectada.</span><span class="sxs-lookup"><span data-stu-id="d3945-115">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="d3945-116">Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="d3945-116">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="d3945-117">Optar pelo suporte a toque/caneta com base em WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="d3945-117">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="d3945-118">Os desenvolvedores que desejam habilitar essa pilha podem adicionar o seguinte ao arquivo de *app.config* do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d3945-118">Developers who wish to enable this stack can add the following to their application's *app.config* file.</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="d3945-119">Remover esta entrada ou definir seu valor como `false` desabilita essa pilha opcional.</span><span class="sxs-lookup"><span data-stu-id="d3945-119">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="d3945-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3945-120">See also</span></span>

- [<span data-ttu-id="d3945-121">Compatibilidade de aplicativos</span><span class="sxs-lookup"><span data-stu-id="d3945-121">Application compatibility</span></span>](application-compatibility.md)
