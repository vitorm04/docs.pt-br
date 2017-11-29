---
title: Reconhecimento de manuscrito
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f8a202d4698c968a91a3d930138290cedfe3a83b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2017
---
# <a name="handwriting-recognition"></a>Reconhecimento de manuscrito
Esta seção discute os fundamentos de reconhecimento relacionada à tinta digital na plataforma do WPF.  
  
## <a name="recognition-solutions"></a>Soluções de reconhecimento  
 O exemplo a seguir mostra como reconhecer tinta utilizando o [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) classe.  
  
> [!NOTE]
>  Este exemplo requer que os reconhecedores de manuscrito esteja instalado no sistema.  
  
 Criar um novo projeto de aplicativo do WPF no Visual Studio chamado **InkRecognition**. Substitua o conteúdo do arquivo Window1 com o seguinte código XAML. Esse código processa a interface do usuário do aplicativo.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Adicione uma referência ao assembly Microsoft Ink, Microsoft.Ink.dll, que pode ser encontrado em \Program Files\Microsoft Shared\Ink. Substitua o conteúdo do arquivo code-behind com o código a seguir.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
