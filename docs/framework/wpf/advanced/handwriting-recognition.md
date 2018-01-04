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
ms.workload: dotnet
ms.openlocfilehash: 384f21587c29e6afe82964fc28432f5a6be92b05
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="handwriting-recognition"></a><span data-ttu-id="2e056-102">Reconhecimento de manuscrito</span><span class="sxs-lookup"><span data-stu-id="2e056-102">Handwriting Recognition</span></span>
<span data-ttu-id="2e056-103">Esta seção discute os fundamentos de reconhecimento relacionada à tinta digital na plataforma do WPF.</span><span class="sxs-lookup"><span data-stu-id="2e056-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="2e056-104">Soluções de reconhecimento</span><span class="sxs-lookup"><span data-stu-id="2e056-104">Recognition Solutions</span></span>  
 <span data-ttu-id="2e056-105">O exemplo a seguir mostra como reconhecer tinta utilizando o [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="2e056-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2e056-106">Este exemplo requer que os reconhecedores de manuscrito esteja instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="2e056-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="2e056-107">Criar um novo projeto de aplicativo do WPF no Visual Studio chamado **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="2e056-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="2e056-108">Substitua o conteúdo do arquivo Window1 com o seguinte código XAML.</span><span class="sxs-lookup"><span data-stu-id="2e056-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="2e056-109">Esse código processa a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2e056-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="2e056-110">Adicione uma referência ao assembly Microsoft Ink, Microsoft.Ink.dll, que pode ser encontrado em \Program Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="2e056-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="2e056-111">Substitua o conteúdo do arquivo code-behind com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2e056-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2e056-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2e056-112">See Also</span></span>  
 <span data-ttu-id="2e056-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="2e056-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
