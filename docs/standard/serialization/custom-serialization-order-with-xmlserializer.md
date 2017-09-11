---
title: "Ordem de serialização personalizada com o XmlSerializer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 975abd20-2a1d-42db-aed3-e898025ccce7
caps.latest.revision: 9
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: fe68a521b8a27f4dd6e5ca9a190a0d37c0ff6410
ms.contentlocale: pt-br
ms.lasthandoff: 08/21/2017

---
# <a name="custom-serialization-order-with-xmlserializer"></a><span data-ttu-id="da738-102">Ordem de serialização personalizada com o XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="da738-102">Custom Serialization Order With XmlSerializer</span></span>
[<span data-ttu-id="da738-103">Baixar Exemplo</span><span class="sxs-lookup"><span data-stu-id="da738-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/CustomOrder.zip.exe)  
  
 <span data-ttu-id="da738-104">Esse exemplo mostra como controlar a ordem de elementos serializados e desserializados para serialização de XML.</span><span class="sxs-lookup"><span data-stu-id="da738-104">This sample shows how to control the order of serialized and deserialized elements for XML serialization.</span></span>  
  
 <span data-ttu-id="da738-105">Revise os comentários no código de origem e nos arquivos build.proj para obter mais informações sobre serialização.</span><span class="sxs-lookup"><span data-stu-id="da738-105">Review comments in the source code and build.proj files for more information on serialization.</span></span>  
  
### <a name="to-build-the-sample-using-the-command-prompt"></a><span data-ttu-id="da738-106">Para criar o exemplo usando o Prompt de Comando</span><span class="sxs-lookup"><span data-stu-id="da738-106">To build the sample using the Command Prompt</span></span>  
  
1.  <span data-ttu-id="da738-107">Abra a janela do Prompt de Comando e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="da738-107">Open the Command Prompt window and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="da738-108">Digite **msbuild CustomOrder.sln** na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="da738-108">Type **msbuild CustomOrder.sln** at the command line.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="da738-109">Para criar o exemplo usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="da738-109">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="da738-110">Abra o [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] e navegue para um dos subdiretórios específicos da linguagem para o exemplo.</span><span class="sxs-lookup"><span data-stu-id="da738-110">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to one of the language-specific subdirectories for the sample.</span></span>  
  
2.  <span data-ttu-id="da738-111">Clique duas vezes no ícone para o CustomOrder.sln para abrir o arquivo no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="da738-111">Double-click the icon for the CustomOrder.sln to open the file in Visual Studio.</span></span>  
  
3.  <span data-ttu-id="da738-112">No menu **Compilar**, selecione **Compilar Solução**.</span><span class="sxs-lookup"><span data-stu-id="da738-112">In the **Build** menu, select **Build Solution**.</span></span>  
  
4.  <span data-ttu-id="da738-113">O aplicativo de exemplo será criado no subdiretório padrão \bin ou \bin\Debug.</span><span class="sxs-lookup"><span data-stu-id="da738-113">The sample application is built in the default \bin or \bin\Debug subdirectory.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da738-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da738-114">See Also</span></span>  
 <span data-ttu-id="da738-115">[Serialização Básica](../../../docs/standard/serialization/basic-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="da738-115">[Basic Serialization](../../../docs/standard/serialization/basic-serialization.md) </span></span>  
 <span data-ttu-id="da738-116">[Serialização Binária](../../../docs/standard/serialization/binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="da738-116">[Binary Serialization](../../../docs/standard/serialization/binary-serialization.md) </span></span>  
 <span data-ttu-id="da738-117">[Controlando a serialização XML usando atributos](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) </span><span class="sxs-lookup"><span data-stu-id="da738-117">[Controlling XML Serialization Using Attributes](../../../docs/standard/serialization/controlling-xml-serialization-using-attributes.md) </span></span>  
 <span data-ttu-id="da738-118">[Apresentando a serialização XML](../../../docs/standard/serialization/introducing-xml-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="da738-118">[Introducing XML Serialization](../../../docs/standard/serialization/introducing-xml-serialization.md) </span></span>  
 <span data-ttu-id="da738-119">[Serialização](../../../docs/standard/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="da738-119">[Serialization](../../../docs/standard/serialization/index.md) </span></span>  
 [<span data-ttu-id="da738-120">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="da738-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)

