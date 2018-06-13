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
ms.openlocfilehash: d72d8b42a23205d8599b23a467677dd2f05d5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542370"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="33276-102">Reconhecimento de manuscrito</span><span class="sxs-lookup"><span data-stu-id="33276-102">Handwriting Recognition</span></span>
<span data-ttu-id="33276-103">Esta seção discute os fundamentos de reconhecimento relacionada à tinta digital na plataforma do WPF.</span><span class="sxs-lookup"><span data-stu-id="33276-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="33276-104">Soluções de reconhecimento</span><span class="sxs-lookup"><span data-stu-id="33276-104">Recognition Solutions</span></span>  
 <span data-ttu-id="33276-105">O exemplo a seguir mostra como reconhecer tinta utilizando o [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) classe.</span><span class="sxs-lookup"><span data-stu-id="33276-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33276-106">Este exemplo requer que os reconhecedores de manuscrito esteja instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="33276-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="33276-107">Criar um novo projeto de aplicativo do WPF no Visual Studio chamado **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="33276-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="33276-108">Substitua o conteúdo do arquivo Window1 com o seguinte código XAML.</span><span class="sxs-lookup"><span data-stu-id="33276-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="33276-109">Esse código processa a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33276-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="33276-110">Adicione uma referência ao assembly Microsoft Ink, Microsoft.Ink.dll, que pode ser encontrado em \Program Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="33276-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="33276-111">Substitua o conteúdo do arquivo code-behind com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="33276-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="33276-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="33276-112">See Also</span></span>  
 <span data-ttu-id="33276-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="33276-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
