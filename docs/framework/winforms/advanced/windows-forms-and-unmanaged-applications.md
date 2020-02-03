---
title: Aplicativos não gerenciados
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: 17dc20653d1628dfd460a9891e1b0a21c0ebecbd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746362"
---
# <a name="windows-forms-and-unmanaged-applications"></a>Windows Forms e aplicativos não gerenciados
Aplicativos do Windows Forms e controles podem interoperar com aplicativos não gerenciados, com algumas restrições. As seções a seguir descrevem os cenários e as configurações com suporte em controles e aplicativos do Windows Forms e aqueles que não têm suporte.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados](windows-forms-and-unmanaged-applications-overview.md)  
 Oferece informações gerais sobre como usar e implementar controles de Windows Forms que funcionam com aplicativos não gerenciados.  
  
 [Como dar suporte à interoperabilidade COM exibindo um Windows Form com o método ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)  
 Fornece um exemplo de código que mostra como usar o método <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> para executar um formulário do Windows em um aplicativo não gerenciado.  
  
 [Como Dar Suporte à Interoperabilidade COM Exibindo Cada Formulário dos Windows Forms em um Thread Separado](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 Fornece um exemplo de código que mostra como executar um formulário do Windows em seu próprio thread.  
  
 Consulte também [Instruções passo a passo: dando suporte à interoperabilidade COM exibindo cada Windows Form no próprio thread](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 Usado para criar um thread separado para um formulário do Windows.  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 Inicia um loop de mensagem para um thread.  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 Realiza marshaling de chamadas de um aplicativo não gerenciado para um formulário.  
  
## <a name="related-sections"></a>Seções Relacionadas  
 [Expondo componentes do .NET Framework ao COM](../../interop/exposing-dotnet-components-to-com.md)  
 Oferece informações gerais sobre como usar tipos de .NET Framework em aplicativos não gerenciados.
