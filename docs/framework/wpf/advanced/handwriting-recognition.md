---
title: Reconhecimento de manuscrito
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: 8f520b80970bfeebdfea01a6c722634efd99ffe7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725383"
---
# <a name="handwriting-recognition"></a>Reconhecimento de manuscrito
Esta seção aborda os conceitos básicos do reconhecimento relacionada à tinta digital na plataforma do WPF.  
  
## <a name="recognition-solutions"></a>Soluções de reconhecimento  
 O exemplo a seguir mostra como reconhecer tinta usando o [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) classe.  
  
> [!NOTE]
>  Este exemplo requer que os reconhecedores de manuscrito seja instalado no sistema.  
  
 Criar um novo projeto de aplicativo do WPF no Visual Studio chamado **InkRecognition**. Substitua o conteúdo do arquivo Window1.xaml pelo seguinte código XAML. Esse código renderiza a interface do usuário do aplicativo.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Adicione uma referência ao assembly Microsoft Ink, Ink, que pode ser encontrado em \Program Files\Microsoft Shared\Ink. Substitua o conteúdo do arquivo code-behind com o código a seguir.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também
- [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
