---
title: Usando controles WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5e616019d53648058d51a3d0df457b1380aaf3b1
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="using-wpf-controls"></a>Usando controles WPF
Você pode usar controles do WPF (Windows Presentation Foundation) em seus aplicativos do Windows Forms. Embora essas sejam duas tecnologias de exibição diferentes, elas interoperam com harmonia.  
  
 O Designer de Formulários do Windows fornece um ambiente de design visual para hospedar controles do Windows Presentation Foundation. Um controle WPF é hospedado por um controle de formulários do Windows especial chamado <xref:System.Windows.Forms.Integration.ElementHost>. Esse controle permite que o controle WPF participe do layout do formulário e receba mensagens de teclado e mouse. Em tempo de design, você pode organizar o <xref:System.Windows.Forms.Integration.ElementHost> controlar exatamente como faria com qualquer controle de formulários do Windows.  
  
 Você também pode usar controles do Windows Forms em seus aplicativos do WPF. Para obter mais informações, consulte [Designer de WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como copiar e colar um controle ElementHost no tempo de design](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Mostra como copiar um controle Windows Presentation Foundation em um Windows Form.  
  
 [Instruções passo a passo: organizando conteúdo WPF no Windows Forms no tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Mostra como usar os recursos de layout do Windows Forms, como ancoragem e guias de alinhamento para organizar controles do Windows Presentation Foundation.  
  
 [Instruções passo a passo: alterando propriedades de um elemento WPF hospedado no tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Mostra o fluxo de trabalho entre o Designer de Formulários do Windows e o [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] para alterar as propriedades de controles WPF.  
  
 [Instruções passo a passo: criando novo conteúdo WPF no Windows Forms no tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Mostra como criar um controle do Windows Presentation Foundation para uso em aplicativos do Windows Forms.  
  
 [Instruções passo a passo: copiando e colando um controle ElementHost em Windows Forms separados](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Mostra como copiar um controle do Windows Presentation Foundation de um Windows Form para outro.  
  
 [Instruções passo a passo: atribuindo conteúdo WPF no Windows Forms no tempo de design](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Mostra como selecionar os tipos de controle do Windows Presentation Foundation que você deseja exibir em seu formulário.  
  
 [Instruções passo a passo: estilos de conteúdo WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Mostra o fluxo de trabalho entre o Designer de Formulários do Windows e o [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] para aplicar estilos aos controles do Windows Presentation Foundation.  
  
## <a name="reference"></a>Referência  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 Descreve uma classe que você pode usar para hospedar os controles do Windows Presentation Foundation em seus aplicativos do Windows Forms.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 Descreve uma classe que você pode usar para hospedar controles do Windows Forms no seu aplicativo do Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Migração e interoperabilidade](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Descreve a interoperação entre as tecnologias Windows Presentation Foundation e Windows Forms.  
  
 [Designer do WPF](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 Descreve como criar controles do Windows Presentation Foundation em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].
