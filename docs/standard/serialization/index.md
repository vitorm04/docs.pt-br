---
title: Serialização-.NET
description: Este artigo fornece informações sobre as tecnologias de serialização do .NET, incluindo serialização binária, serialização de XML e SOAP e serialização JSON.
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: b3d76c14dc9180a5f19781122d1a42bcae603e76
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "83377241"
---
# <a name="serialization-in-net"></a><span data-ttu-id="f5bbf-103">Serialização no .NET</span><span class="sxs-lookup"><span data-stu-id="f5bbf-103">Serialization in .NET</span></span>

<span data-ttu-id="f5bbf-104">A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-104">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="f5bbf-105">O complemento de serialização é desserialização, que converte um fluxo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-105">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="f5bbf-106">Juntos, esses processos permitem que os dados sejam armazenados e transferidos.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-106">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="f5bbf-107">O .NET apresenta as seguintes tecnologias de serialização:</span><span class="sxs-lookup"><span data-stu-id="f5bbf-107">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="f5bbf-108">A [serialização binária](binary-serialization.md) preserva a fidelidade do tipo, que é útil para preservar o estado de um objeto entre diferentes invocações de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-108">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="f5bbf-109">Por exemplo, você pode compartilhar um objeto entre diferentes aplicativos serializando-o para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-109">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="f5bbf-110">Você pode serializar um objeto para um fluxo, um disco, a memória, pela rede, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-110">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="f5bbf-111">O acesso remoto usa a serialização para passar objetos “por valor” de um computador ou domínio de aplicativo para outro.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-111">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="f5bbf-112">A [serialização de XML e SOAP](xml-and-soap-serialization.md) serializa apenas campos e propriedades públicas e não preserva a fidelidade do tipo.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-112">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="f5bbf-113">Isso é útil quando você deseja fornecer ou consumir dados sem restringir o aplicativo que usa os dados.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-113">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="f5bbf-114">Como o XML é um padrão aberto, é uma opção atrativa para compartilhar dados pela Web.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-114">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="f5bbf-115">SOAP é, da mesma forma, um padrão aberto, uma opção atrativa.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-115">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="f5bbf-116">A [serialização JSON](system-text-json-overview.md) serializa apenas as propriedades públicas e não preserva a fidelidade do tipo.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-116">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="f5bbf-117">JSON é um padrão aberto que é uma opção atraente para compartilhar dados na Web.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-117">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="f5bbf-118">Referência</span><span class="sxs-lookup"><span data-stu-id="f5bbf-118">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="f5bbf-119">Contém classes que podem ser usadas para serialização e desserialização de objetos.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-119">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="f5bbf-120">Contém classes que podem ser usadas para serializar objetos em documentos ou fluxos de formato XML.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-120">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="f5bbf-121">Contém classes que podem ser usadas para serializar objetos em fluxos ou documentos de formato JSON.</span><span class="sxs-lookup"><span data-stu-id="f5bbf-121">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
