---
title: Ordem de serialização personalizada com o XmlSerializer
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b091d07ada0031013c935c5ab12b77ebedd6bcc3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="559af-102">Ordem de serialização personalizada com o XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="559af-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="559af-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="559af-103">Download Sample</span></span>](https://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="559af-104">Esse exemplo mostra como controlar a ordem de elementos serializados e desserializados para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="559af-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="559af-105">Revise os comentários no código de origem e nos arquivos build.proj para obter mais informações sobre serialização.</span><span class="sxs-lookup"><span data-stu-id="559af-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="559af-106">Para criar o exemplo usando o Prompt de Comando</span><span class="sxs-lookup"><span data-stu-id="559af-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="559af-107">Abra a janela do Prompt de Comando e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="559af-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="559af-108">Digite **msbuild CustomOrder.sln** na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="559af-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="559af-109">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="559af-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="559af-110">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="559af-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="559af-111">Clique duas vezes no ícone para o CustomOrder.sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="559af-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="559af-112">No menu **Compilar**, selecione **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="559af-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="559af-113">O aplicativo de exemplo será criado no subdiretório padrão \bin ou \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="559af-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="559af-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="559af-114">See Also</span></span>  
 [<span data-ttu-id="559af-115">Serialização básica</span><span class="sxs-lookup"><span data-stu-id="559af-115">Basic Serialization</span></span>](../../../docs/standard/serialization/basic-serialization.md)  
 [<span data-ttu-id="559af-116">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="559af-116">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
 [<span data-ttu-id="559af-117">Controlando a serialização XML usando atributos</span><span class="sxs-lookup"><span data-stu-id="559af-117">Controlling XML Serialization Using Attributes</span></span>](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md)  
 [<span data-ttu-id="559af-118">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="559af-118">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="559af-119">Serialização</span><span class="sxs-lookup"><span data-stu-id="559af-119">Serialization</span></span>](../../../docs/standard/serialization/index.md)  
 [<span data-ttu-id="559af-120">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="559af-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
