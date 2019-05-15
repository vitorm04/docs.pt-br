---
title: Serialização no .NET
ms.date: 03/30/2017
helpviewer_keywords:
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: 1f90a128ef6b29acbd315beae7aaaf1d1b78a62b
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638856"
---
# <a name="serialization-in-net"></a><span data-ttu-id="940c4-102">Serialização no .NET</span><span class="sxs-lookup"><span data-stu-id="940c4-102">Serialization in .NET</span></span>
<span data-ttu-id="940c4-103">A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado.</span><span class="sxs-lookup"><span data-stu-id="940c4-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="940c4-104">O complemento de serialização é desserialização, que converte um fluxo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="940c4-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="940c4-105">Juntos, esses processos permitem que os dados sejam facilmente armazenados e transferidos.</span><span class="sxs-lookup"><span data-stu-id="940c4-105">Together, these processes allow data to be easily stored and transferred.</span></span>  
  
<span data-ttu-id="940c4-106">O .NET conta com duas tecnologias de serialização:</span><span class="sxs-lookup"><span data-stu-id="940c4-106">.NET features two serialization technologies:</span></span>  
  
- <span data-ttu-id="940c4-107">A serialização binária preserva a fidelidade do tipo, que é útil para preservar o estado de um objeto entre diferentes chamadas de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="940c4-107">Binary serialization preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="940c4-108">Por exemplo, você pode compartilhar um objeto entre diferentes aplicativos serializando-o para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="940c4-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="940c4-109">Você pode serializar um objeto para um fluxo, um disco, a memória, pela rede, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="940c4-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="940c4-110">O acesso remoto usa a serialização para passar objetos “por valor” de um computador ou domínio de aplicativo para outro.</span><span class="sxs-lookup"><span data-stu-id="940c4-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="940c4-111">A serialização XML serializa somente as propriedades públicas e os campos e não preserva a fidelidade de tipo.</span><span class="sxs-lookup"><span data-stu-id="940c4-111">XML serialization serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="940c4-112">Isso é útil quando você deseja fornecer ou consumir dados sem restringir o aplicativo que usa os dados.</span><span class="sxs-lookup"><span data-stu-id="940c4-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="940c4-113">Como o XML é um padrão aberto, é uma opção atrativa para compartilhar dados pela Web.</span><span class="sxs-lookup"><span data-stu-id="940c4-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="940c4-114">SOAP é, da mesma forma, um padrão aberto, uma opção atrativa.</span><span class="sxs-lookup"><span data-stu-id="940c4-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="940c4-115">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="940c4-115">In This Section</span></span>  
[<span data-ttu-id="940c4-116">Tópicos com instruções de serialização</span><span class="sxs-lookup"><span data-stu-id="940c4-116">Serialization How-to Topics</span></span>](../../../docs/standard/serialization/serialization-how-to-topics.md)  
<span data-ttu-id="940c4-117">As listas vinculam tópicos de Como fazer contidas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="940c4-117">Lists links to How-to topics contained in this section.</span></span>
  
[<span data-ttu-id="940c4-118">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="940c4-118">Binary Serialization</span></span>](../../../docs/standard/serialization/binary-serialization.md)  
<span data-ttu-id="940c4-119">Descreve o mecanismo de serialização binária que está incluído com o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="940c4-119">Describes the binary serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="940c4-120">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="940c4-120">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
<span data-ttu-id="940c4-121">Descreve o mecanismo de serialização de XML e SOAP que está incluído com o Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="940c4-121">Describes the XML and SOAP serialization mechanism that is included with the common language runtime.</span></span>

[<span data-ttu-id="940c4-122">Ferramentas de serialização</span><span class="sxs-lookup"><span data-stu-id="940c4-122">Serialization Tools</span></span>](../../../docs/standard/serialization/serialization-tools.md)  
<span data-ttu-id="940c4-123">Essas ferramentas ajudam a desenvolver código de serialização.</span><span class="sxs-lookup"><span data-stu-id="940c4-123">These tools help develop serialization code.</span></span>

[<span data-ttu-id="940c4-124">Exemplos de serialização</span><span class="sxs-lookup"><span data-stu-id="940c4-124">Serialization Samples</span></span>](../../../docs/standard/serialization/serialization-samples.md)  
<span data-ttu-id="940c4-125">Os exemplos demonstram como fazer a serialização.</span><span class="sxs-lookup"><span data-stu-id="940c4-125">The samples demonstrate how to do serialization.</span></span>

## <a name="reference"></a><span data-ttu-id="940c4-126">Referência</span><span class="sxs-lookup"><span data-stu-id="940c4-126">Reference</span></span>
<span data-ttu-id="940c4-127">O <xref:System.Runtime.Serialization> contém classes que podem ser usadas para serialização e desserialização de objetos.</span><span class="sxs-lookup"><span data-stu-id="940c4-127"><xref:System.Runtime.Serialization> Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="940c4-128">Contém classes que podem ser usadas para serializar objetos em documentos ou fluxos de formato XML.</span><span class="sxs-lookup"><span data-stu-id="940c4-128">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>
