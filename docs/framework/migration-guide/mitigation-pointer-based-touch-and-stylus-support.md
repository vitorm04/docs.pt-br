---
title: 'Mitigação: suporte a toque e caneta com base em ponteiro'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da7d55b34bc21f0c11f13565d017587b4276bad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387774"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="9a8e0-102">Mitigação: suporte a toque e caneta com base em ponteiro</span><span class="sxs-lookup"><span data-stu-id="9a8e0-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="9a8e0-103">Os aplicativos do WPF que se destinam ao .NET Framework 4.7 e estão em execução em sistemas Windows a partir da Atualização do Windows 10 para Criadores podem habilitar uma pilha opcional de toque/caneta do WPF com base em `WM_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="9a8e0-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="9a8e0-104">Impact</span></span>

<span data-ttu-id="9a8e0-105">Os desenvolvedores que não habilitarem explicitamente o suporte a toque/caneta com base em ponteiro não verão nenhuma alteração no comportamento de toque/caneta do WPF.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="9a8e0-106">A seguir estão os problemas conhecidos no momento com a pilha de toque/caneta com base em `WM_POINTER` opcional:</span><span class="sxs-lookup"><span data-stu-id="9a8e0-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="9a8e0-107">Não há suporte para escrita à tinta em tempo real.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-107">No support for real-time inking.</span></span>

   <span data-ttu-id="9a8e0-108">Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles são processados no thread da interface do usuário, o que pode levar a um desempenho ruim.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="9a8e0-109">Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="9a8e0-110">A manipulação pode se comportar de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="9a8e0-111">Arrastar/soltar não mostrará comentários apropriados para entrada por toque.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="9a8e0-112">(Isso não afeta entrada de caneta).</span><span class="sxs-lookup"><span data-stu-id="9a8e0-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="9a8e0-113">Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="9a8e0-114">Isso pode travar o aplicativo até que a entrada do mouse seja detectada.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-114">This can potentially hang the application until mouse input is detected.</span></span> <span data-ttu-id="9a8e0-115">Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a><span data-ttu-id="9a8e0-116">Optar pelo suporte a toque/caneta com base em WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="9a8e0-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="9a8e0-117">Os desenvolvedores que desejam habilitar essa pilha podem adicionar o seguinte ao arquivo app.config do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="9a8e0-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="9a8e0-118">Remover esta entrada ou definir seu valor como `false` desabilita essa pilha opcional.</span><span class="sxs-lookup"><span data-stu-id="9a8e0-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="9a8e0-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a8e0-119">See also</span></span>

[<span data-ttu-id="9a8e0-120">Alterações de redirecionamento no .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="9a8e0-120">Retargeting Changes in the .NET Framework 4.7</span></span>](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
