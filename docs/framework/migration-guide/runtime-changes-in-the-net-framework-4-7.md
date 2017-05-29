---
title: "Alterações de tempo de execução no .NET Framework 4.7 | Microsoft Docs"
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- runtime changes,.NET Framework
- runtime changes,.NET Framework 4.7
- application compatibility
ms.assetid: 268eb334-7906-4e0b-a1e3-c74b745de2a5
caps.latest.revision: 8
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: fccd83571b47e3c2a6f995893c6260ae91eae517
ms.openlocfilehash: e114f15adb9ed18d7ee2ba857013959b2710e70c
ms.contentlocale: pt-br
ms.lasthandoff: 05/22/2017

---
# <a name="runtime-changes-in-the-net-framework-47"></a>Alterações de tempo de execução no .NET Framework 4.7

Em casos raros, as alterações de tempo de execução podem afetar aplicativos existentes direcionados a versões anteriores do .NET Framework, mas que são executados em uma versão posterior do tempo de execução do .NET Framework. Elas também incluem diferenças no comportamento entre aplicativos que são executados em diferentes ambientes de tempo de execução do .NET Framework. O .NET Framework 4.6.2 inclui alterações nas seguintes áreas:

- [Windows Presentation Foundation (WPF)](#WPF)

A coluna Escopo nas tabelas a seguir especifica o significado de cada alteração:

- Principal. Uma alteração significativa que afeta um grande número de aplicativos ou que exige a modificação significativa do código. Observe que nenhuma das alterações de redirecionamento entra nessa categoria.

- Secundário. Uma alteração que afeta um pequeno número de aplicativos ou que exige a modificação secundária do código.

- Borda. Uma alteração que afeta aplicativos em cenários muito específicos que não são comuns.

- Transparente. Uma alteração que não tem efeito visível para o desenvolvedor ou o usuário do aplicativo. O aplicativo não deve exigir modificação por conta dessa alteração.

## <a name="a-namewpf--windows-presentation-foundation-wpf"></a><a name="WPF" /> WPF (Windows Presentation Foundation)

<xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView(System.Int32)>

| Recurso | Alteração | Impacto | Escopo |
|---|---|---|---|
| <xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> method | No .NET Framework 4.6.2, o método <xref:System.Windows.Controls.DataGridCellsPanel.BringIndexIntoView%2A> é executado de forma assíncrona quando virtualização de coluna está habilitada, mas as larguras das colunas não foram determinadas. Se as colunas forem removidas antes que a operação assíncrona seja concluída, um <xref:System.ArgumentOutOfRangeException> poderá ocorrer.<br/></br>A partir do .NET Framework 4.7, a exceção não é mais gerada neste cenário. | Essa alteração aumenta a confiabilidade do método. | Edge | 
|Tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup> | No .NET Framework 4.6.2 e nas versões anteriores, a tela de fundo <xref:System.Windows.Controls.Ribbon.RibbonGroup> em builds localizados era pintada com um pincel transparente, resultando em uma experiência ruim da interface do usuário. No .NET Framework 4.7, o WPF atualiza os recursos localizados do controle <xref:System.Windows.Controls.Ribbon.RibbonGroup>, o que garante que o pincel correto seja selecionado. | Para aproveitar o novo comportamento, atualize para o .NET Framework 4.7. | Edge |
| Verificador ortográfico do WPF | A partir do .NET Framework 4.6.1, o verificador ortográfico em aplicativos WPF ocasionalmente gera uma <xref:System.ObjectDisposedException>durante o desligamento do aplicativo. <br/><br/>No .NET Framework 4.7, a exceção é tratada normalmente pelo tempo de execução, garantindo que os aplicativos não sejam são afetados negativamente. Observe que exceções de primeira chance ocasionais continuam a ser observadas em aplicativos em execução em um depurador.  | Para aproveitar o novo comportamento, atualize para o .NET Framework 4.7.   | Edge |

## <a name="see-also"></a>Consulte também

[Compatibilidade de aplicativos no .NET Framework 4.7](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-7.md)


