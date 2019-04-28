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
# <a name="handwriting-recognition"></a><span data-ttu-id="069c2-102">Reconhecimento de manuscrito</span><span class="sxs-lookup"><span data-stu-id="069c2-102">Handwriting Recognition</span></span>
<span data-ttu-id="069c2-103">Esta seção aborda os conceitos básicos do reconhecimento relacionada à tinta digital na plataforma do WPF.</span><span class="sxs-lookup"><span data-stu-id="069c2-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="069c2-104">Soluções de reconhecimento</span><span class="sxs-lookup"><span data-stu-id="069c2-104">Recognition Solutions</span></span>  
 <span data-ttu-id="069c2-105">O exemplo a seguir mostra como reconhecer tinta usando o [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) classe.</span><span class="sxs-lookup"><span data-stu-id="069c2-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="069c2-106">Este exemplo requer que os reconhecedores de manuscrito seja instalado no sistema.</span><span class="sxs-lookup"><span data-stu-id="069c2-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="069c2-107">Criar um novo projeto de aplicativo do WPF no Visual Studio chamado **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="069c2-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="069c2-108">Substitua o conteúdo do arquivo Window1.xaml pelo seguinte código XAML.</span><span class="sxs-lookup"><span data-stu-id="069c2-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="069c2-109">Esse código renderiza a interface do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="069c2-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="069c2-110">Adicione uma referência ao assembly Microsoft Ink, Ink, que pode ser encontrado em \Program Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="069c2-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="069c2-111">Substitua o conteúdo do arquivo code-behind com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="069c2-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="069c2-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="069c2-112">See also</span></span>

- <span data-ttu-id="069c2-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="069c2-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span></span>
