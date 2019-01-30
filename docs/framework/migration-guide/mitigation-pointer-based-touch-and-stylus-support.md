---
title: 'Mitigação: Suporte para toque e caneta baseado em ponteiro'
ms.date: 04/07/2017
helpviewer_keywords:
- retargeting changes
- .NET Framework 4.7 retargeting changes
- WPF retargeting changes
- WPF pointer-based touch and stylus stack
ms.assetid: f99126b5-c396-48f9-8233-8f36b4c9e717
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d750087cc000ad31a24d91411c0885a75d59e74f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501932"
---
# <a name="mitigation-pointer-based-touch-and-stylus-support"></a>Mitigação: Suporte para toque e caneta baseado em ponteiro

Os aplicativos do WPF que se destinam ao .NET Framework 4.7 e estão em execução em sistemas Windows a partir da Atualização do Windows 10 para Criadores podem habilitar uma pilha opcional de toque/caneta do WPF com base em `WM_POINTER`.

## <a name="impact"></a>Impacto

Os desenvolvedores que não habilitarem explicitamente o suporte a toque/caneta com base em ponteiro não verão nenhuma alteração no comportamento de toque/caneta do WPF.

A seguir estão os problemas conhecidos no momento com a pilha de toque/caneta com base em `WM_POINTER` opcional:

- Não há suporte para escrita à tinta em tempo real.

   Embora os plug-ins de caneta e escrita à tinta ainda funcionem, eles são processados no thread da interface do usuário, o que pode levar a um desempenho ruim.

- Alterações de comportamento devido a alterações na promoção de eventos de toque/caneta para eventos de mouse.

  - A manipulação pode se comportar de maneira diferente.

  - Arrastar/soltar não mostrará comentários apropriados para entrada por toque. (Isso não afeta entrada de caneta).

  - Arrastar/soltar não pode mais ser iniciado em eventos de toque/caneta.

      Isso pode travar o aplicativo até que a entrada do mouse seja detectada. Em vez disso, os desenvolvedores devem iniciar a ação de arrastar e soltar usando eventos de mouse.

## <a name="opting-in-to-wmpointer-based-touchstylus-support"></a>Optar pelo suporte a toque/caneta com base em WM_POINTER

Os desenvolvedores que desejam habilitar essa pilha podem adicionar o seguinte ao arquivo app.config do aplicativo:

```xml
<configuration>
    <runtime>
        <AppContextSwitchOverrides value="Switch.System.Windows.Input.Stylus.EnablePointerSupport=true"/>
    </runtime>
</configuration>
```

Remover esta entrada ou definir seu valor como `false` desabilita essa pilha opcional.

## <a name="see-also"></a>Consulte também

- [Alterações de redirecionamento no .NET Framework 4.7](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md)
