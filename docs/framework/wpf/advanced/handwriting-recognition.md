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
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956524"
---
# <a name="handwriting-recognition"></a>Reconhecimento de manuscrito
Esta seção aborda os conceitos básicos do reconhecimento que pertencem à tinta digital na plataforma WPF.  
  
## <a name="recognition-solutions"></a>Soluções de reconhecimento  
 O exemplo a seguir mostra como reconhecer a tinta usando a classe [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .  
  
> [!NOTE]
> Este exemplo requer que os reconhecedores de manuscrito estejam instalados no sistema.  
  
 Crie um novo projeto de aplicativo WPF no Visual Studio chamado **InkRecognition**. Substitua o conteúdo do arquivo Window1. XAML pelo código XAML a seguir. Esse código processa a interface do usuário do aplicativo.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Adicione uma referência ao assembly de tinta da Microsoft, Microsoft. Ink. dll, que pode ser encontrado em \Program Files\Common Files\Microsoft Shared\Ink. Substitua o conteúdo do arquivo code-behind pelo código a seguir.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Consulte também

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
