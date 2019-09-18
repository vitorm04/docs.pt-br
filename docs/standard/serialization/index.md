---
title: Serialização-.NET
ms.date: 09/02/2019
helpviewer_keywords:
- JSON serialization
- XML serialization, defined
- binary serialization
- serializing objects
- serialization
- objects, serializing
ms.assetid: 4d1111c0-9447-4231-a997-96a2b74b3453
ms.openlocfilehash: e6db24326c79ab6509b253c45c27f87a2aacd73c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053356"
---
# <a name="serialization-in-net"></a><span data-ttu-id="f7540-102">Serialização no .NET</span><span class="sxs-lookup"><span data-stu-id="f7540-102">Serialization in .NET</span></span>

<span data-ttu-id="f7540-103">A serialização é o processo de conversão do estado de um objeto em um formulário que possa ser persistido ou transportado.</span><span class="sxs-lookup"><span data-stu-id="f7540-103">Serialization is the process of converting the state of an object into a form that can be persisted or transported.</span></span> <span data-ttu-id="f7540-104">O complemento de serialização é desserialização, que converte um fluxo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="f7540-104">The complement of serialization is deserialization, which converts a stream into an object.</span></span> <span data-ttu-id="f7540-105">Juntos, esses processos permitem que os dados sejam armazenados e transferidos.</span><span class="sxs-lookup"><span data-stu-id="f7540-105">Together, these processes allow data to be stored and transferred.</span></span>  
  
<span data-ttu-id="f7540-106">O .NET apresenta as seguintes tecnologias de serialização:</span><span class="sxs-lookup"><span data-stu-id="f7540-106">.NET features the following serialization technologies:</span></span>  
  
- <span data-ttu-id="f7540-107">A [serialização binária](binary-serialization.md) preserva a fidelidade do tipo, que é útil para preservar o estado de um objeto entre diferentes invocações de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f7540-107">[Binary serialization](binary-serialization.md) preserves type fidelity, which is useful for preserving the state of an object between different invocations of an application.</span></span> <span data-ttu-id="f7540-108">Por exemplo, você pode compartilhar um objeto entre diferentes aplicativos serializando-o para a área de transferência.</span><span class="sxs-lookup"><span data-stu-id="f7540-108">For example, you can share an object between different applications by serializing it to the Clipboard.</span></span> <span data-ttu-id="f7540-109">Você pode serializar um objeto para um fluxo, um disco, a memória, pela rede, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="f7540-109">You can serialize an object to a stream, to a disk, to memory, over the network, and so forth.</span></span> <span data-ttu-id="f7540-110">O acesso remoto usa a serialização para passar objetos “por valor” de um computador ou domínio de aplicativo para outro.</span><span class="sxs-lookup"><span data-stu-id="f7540-110">Remoting uses serialization to pass objects "by value" from one computer or application domain to another.</span></span>  
  
- <span data-ttu-id="f7540-111">A [serialização de XML e SOAP](xml-and-soap-serialization.md) serializa apenas campos e propriedades públicas e não preserva a fidelidade do tipo.</span><span class="sxs-lookup"><span data-stu-id="f7540-111">[XML and SOAP serialization](xml-and-soap-serialization.md) serializes only public properties and fields and does not preserve type fidelity.</span></span> <span data-ttu-id="f7540-112">Isso é útil quando você deseja fornecer ou consumir dados sem restringir o aplicativo que usa os dados.</span><span class="sxs-lookup"><span data-stu-id="f7540-112">This is useful when you want to provide or consume data without restricting the application that uses the data.</span></span> <span data-ttu-id="f7540-113">Como o XML é um padrão aberto, é uma opção atrativa para compartilhar dados pela Web.</span><span class="sxs-lookup"><span data-stu-id="f7540-113">Because XML is an open standard, it is an attractive choice for sharing data across the Web.</span></span> <span data-ttu-id="f7540-114">SOAP é, da mesma forma, um padrão aberto, uma opção atrativa.</span><span class="sxs-lookup"><span data-stu-id="f7540-114">SOAP is likewise an open standard, which makes it an attractive choice.</span></span>  
  
- <span data-ttu-id="f7540-115">A [serialização JSON](system-text-json-overview.md) serializa apenas as propriedades públicas e não preserva a fidelidade do tipo.</span><span class="sxs-lookup"><span data-stu-id="f7540-115">[JSON serialization](system-text-json-overview.md) serializes only public properties and does not preserve type fidelity.</span></span> <span data-ttu-id="f7540-116">JSON é um padrão aberto que é uma opção atraente para compartilhar dados na Web.</span><span class="sxs-lookup"><span data-stu-id="f7540-116">JSON is an open standard that is an attractive choice for sharing data across the web.</span></span>

## <a name="reference"></a><span data-ttu-id="f7540-117">Referência</span><span class="sxs-lookup"><span data-stu-id="f7540-117">Reference</span></span>

<xref:System.Runtime.Serialization>  
<span data-ttu-id="f7540-118">Contém classes que podem ser usadas para serialização e desserialização de objetos.</span><span class="sxs-lookup"><span data-stu-id="f7540-118">Contains classes that can be used for serializing and deserializing objects.</span></span>
  
<xref:System.Xml.Serialization>  
<span data-ttu-id="f7540-119">Contém classes que podem ser usadas para serializar objetos em documentos ou fluxos de formato XML.</span><span class="sxs-lookup"><span data-stu-id="f7540-119">Contains classes that can be used to serialize objects into XML format documents or streams.</span></span>

<xref:System.Text.Json>  
<span data-ttu-id="f7540-120">Contém classes que podem ser usadas para serializar objetos em fluxos ou documentos de formato JSON.</span><span class="sxs-lookup"><span data-stu-id="f7540-120">Contains classes that can be used to serialize objects into JSON format documents or streams.</span></span>
