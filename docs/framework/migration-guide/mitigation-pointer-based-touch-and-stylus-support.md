---
title: 'Mitigação: suporte a toque e caneta com base em ponteiro'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
ms.openlocfilehash: 41a587b343e4774a27e9ddc39080de6939839d93
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73126196"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a><span data-ttu-id="1bd2a-102">Mitigação: suporte a toque e caneta com base em ponteiro</span><span class="sxs-lookup"><span data-stu-id="1bd2a-102">Mitigation: Pointer-based Touch and Stylus Support</span></span>

<span data-ttu-id="1bd2a-103">Os aplicativos do WPF que se destinam ao .NET Framework 4.7 e estão em execução em sistemas Windows a partir da Atualização do Windows 10 para Criadores podem habilitar uma pilha opcional de toque/caneta do WPF com base em `WM_POINTER`.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-103">WPF applications that target the .NET Framework 4.7 and are running on Windows Systems starting with Windows 10 Creators Update can enable an optional `WM_POINTER`-based WPF touch/stylus stack.</span></span>

## <a name="impact"></a><span data-ttu-id="1bd2a-104">Impacto</span><span class="sxs-lookup"><span data-stu-id="1bd2a-104">Impact</span></span>

<span data-ttu-id="1bd2a-105">Os desenvolvedores que não habilitarem explicitamente o suporte a toque/caneta com base em ponteiro não verão nenhuma alteração no comportamento de toque/caneta do WPF.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-105">Developers who do not explicitly enable pointer-based touch/stylus support should see no change in WPF touch/stylus behavior.</span></span>

<span data-ttu-id="1bd2a-106">A seguir estão os problemas conhecidos no momento com a pilha de toque/caneta com base em `WM_POINTER` opcional:</span><span class="sxs-lookup"><span data-stu-id="1bd2a-106">The following are current known issues with the optional `WM_POINTER`-based touch/stylus stack:</span></span>

- <span data-ttu-id="1bd2a-107">Não há suporte para escrita à tinta em tempo real.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-107">No support for real-time inking.</span></span>

   <span data-ttu-id="1bd2a-108">Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles são processados no thread da interface do usuário, o que pode levar a um desempenho ruim.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-108">While inking and stylus plugins still work, they are processed on the UI thread, which can lead to poor performance.</span></span>

- <span data-ttu-id="1bd2a-109">Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-109">Behavioral changes due to changes in promotion from touch/stylus events to mouse events.</span></span>

  - <span data-ttu-id="1bd2a-110">A manipulação pode se comportar de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-110">Manipulation may behave differently.</span></span>

  - <span data-ttu-id="1bd2a-111">Arrastar/soltar não mostrará comentários apropriados para entrada por toque.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-111">Drag/Drop will not show appropriate feedback for touch input.</span></span> <span data-ttu-id="1bd2a-112">(Isso não afeta entrada de caneta).</span><span class="sxs-lookup"><span data-stu-id="1bd2a-112">(This does not affect stylus input.)</span></span>

  - <span data-ttu-id="1bd2a-113">Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-113">Drag/Drop can no longer be initiated on touch/stylus events.</span></span>

      <span data-ttu-id="1bd2a-114">Isso pode fazer com que o aplicativo pare de responder até que a entrada do mouse seja detectada.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-114">This can potentially cause the application to become unresponsive until mouse input is detected.</span></span> <span data-ttu-id="1bd2a-115">Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-115">Instead, developers should initiate drag and drop from mouse events.</span></span>

## <a name="opting-in-to-wm_pointer-based-touchstylus-support"></a><span data-ttu-id="1bd2a-116">Optar pelo suporte a toque/caneta com base em WM_POINTER</span><span class="sxs-lookup"><span data-stu-id="1bd2a-116">Opting in to WM_POINTER-based touch/stylus support</span></span>

<span data-ttu-id="1bd2a-117">Os desenvolvedores que desejam habilitar essa pilha podem adicionar o seguinte ao arquivo app.config do aplicativo:</span><span class="sxs-lookup"><span data-stu-id="1bd2a-117">Developers who wish to enable this stack can add the following to their application's app.config file:</span></span>

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

<span data-ttu-id="1bd2a-118">Remover esta entrada ou definir seu valor como `false` desabilita essa pilha opcional.</span><span class="sxs-lookup"><span data-stu-id="1bd2a-118">Removing this entry or setting its value to `false` turns this optional stack off.</span></span>

## <a name="see-also"></a><span data-ttu-id="1bd2a-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1bd2a-119">See also</span></span>

- [<span data-ttu-id="1bd2a-120">Alterações de redirecionamento no .NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="1bd2a-120">Retargeting Changes in the .NET Framework 4.7</span></span>](retargeting-changes-in-the-net-framework-4-7.md)
