---
title: Como adicionar uma tela inicial a um aplicativo WPF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 121cbc1c07ea8f6458df81d861aea3f8e1f91086
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Como adicionar uma tela inicial a um aplicativo WPF
Este tópico mostra como adicionar uma janela de inicialização ou *tela inicial*, para um aplicativo do Windows Presentation Foundation (WPF).  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a>Para adicionar uma imagem existente como uma tela inicial  
  
1.  Crie ou localize uma imagem que deseja usar para a tela inicial. Você pode usar qualquer formato de imagem com suporte do Windows Imaging Component (WIC). Por exemplo, você pode usar o formato TIFF, GIF, JPEG, PNG ou BMP.  
  
2.  Adicione o arquivo de imagem ao projeto de aplicativo do WPF. Para obter mais informações, consulte [NIB: como adicionar itens existentes a um projeto](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).  
  
3.  No Gerenciador de Soluções, selecione a imagem.  
  
4.  Na janela Propriedades, clique na seta suspensa para a propriedade **Build Action**.  
  
5.  Selecione **SplashScreen** na lista suspensa.  
  
    > [!NOTE]
    >  Se você não vir a opção **SplashScreen**, certifique-se de verificar se está usando [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 ou posterior.  
  
6.  Pressione F5 para compilar e executar o aplicativo.  
  
     A imagem da tela inicial aparece no centro da tela e, em seguida, desaparece quando a janela principal do aplicativo aparecer.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Para remover a tela inicial de um aplicativo  
  
1.  No Gerenciador de Soluções, selecione a imagem da tela inicial.  
  
2.  Na janela Propriedades, defina **Build Action** como **None**.  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>Para remover a tela inicial de um aplicativo  
  
-   No Gerenciador de Soluções, exclua a imagem da tela inicial.  
  
-   Exclua a imagem da tela inicial do projeto.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.SplashScreen>  
 [NIB: como adicionar itens existentes a um projeto](http://msdn.microsoft.com/library/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
