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
ms.openlocfilehash: 417af272514ac9ce68c8faa72339f2befc2dd7c1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923377"
---
# <a name="handwriting-recognition"></a>Reconhecimento de manuscrito
Esta seção aborda os conceitos básicos do reconhecimento relacionada à tinta digital na plataforma do WPF.  
  
## <a name="recognition-solutions"></a>Soluções de reconhecimento  
 O exemplo a seguir mostra como reconhecer tinta usando o [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) classe.  
  
> [!NOTE]
>  Este exemplo requer que os reconhecedores de manuscrito seja instalado no sistema.  
  
 Criar um novo projeto de aplicativo do WPF no Visual Studio chamado **InkRecognition**. Substitua o conteúdo do arquivo Window1.xaml pelo seguinte código XAML. Esse código renderiza a interface do usuário do aplicativo.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Adicione uma referência ao assembly Microsoft Ink, Ink, que pode ser encontrado em \Program Files\Microsoft Shared\Ink. Substitua o conteúdo do arquivo code-behind com o código a seguir.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
