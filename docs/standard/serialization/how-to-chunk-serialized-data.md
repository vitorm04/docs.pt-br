---
title: Como partir dados serializados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: 6a39997d8854d525146c044ed4bbf939de615d3f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64602429"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="e51ca-102">Como partir dados serializados</span><span class="sxs-lookup"><span data-stu-id="e51ca-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="e51ca-103">Dois problemas que ocorrem ao enviar grandes conjuntos de dados em mensagens de serviço Web são:</span><span class="sxs-lookup"><span data-stu-id="e51ca-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="e51ca-104">Um grande conjunto de trabalho (memória) devido ao armazenamento em buffer pelo mecanismo de serialização.</span><span class="sxs-lookup"><span data-stu-id="e51ca-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="e51ca-105">Consumo de largura de banda desordenado devido à inflação de 33 por cento após a codificação Base64.</span><span class="sxs-lookup"><span data-stu-id="e51ca-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="e51ca-106">Para resolver esses problemas, implemente a interface <xref:System.Xml.Serialization.IXmlSerializable> para controlar a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="e51ca-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="e51ca-107">Especificamente, implemente os métodos <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> e <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> para partir os dados.</span><span class="sxs-lookup"><span data-stu-id="e51ca-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="e51ca-108">Para implementar o agrupamento do lado do servidor</span><span class="sxs-lookup"><span data-stu-id="e51ca-108">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="e51ca-109">Na música do servidor, o método da Web deve desativar o buffer do ASP.NET e retornar um tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="e51ca-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="e51ca-110">O tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable> partir os dados no método <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="e51ca-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="e51ca-111">Para implementar o processamento do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="e51ca-111">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="e51ca-112">Altere o método da Web no proxy do cliente para retornar o tipo que implementa <xref:System.Xml.Serialization.IXmlSerializable>.</span><span class="sxs-lookup"><span data-stu-id="e51ca-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="e51ca-113">Você pode usar uma <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> para fazer isso automaticamente, mas isso não é mostrado aqui.</span><span class="sxs-lookup"><span data-stu-id="e51ca-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="e51ca-114">Implemente o método <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> para ler o fluxo de dados em partes e gravar os bytes no disco.</span><span class="sxs-lookup"><span data-stu-id="e51ca-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="e51ca-115">Essa implementação também gera eventos de progresso que podem ser usados por um controle de gráfico, como uma barra de progresso.</span><span class="sxs-lookup"><span data-stu-id="e51ca-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e51ca-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e51ca-116">Example</span></span>  
<span data-ttu-id="e51ca-117">O exemplo de código a seguir mostra o método da Web no cliente que desativa o buffering do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e51ca-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="e51ca-118">Ele também mostra a implementação do lado do cliente da interface <xref:System.Xml.Serialization.IXmlSerializable> que parte os dados no método <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>.</span><span class="sxs-lookup"><span data-stu-id="e51ca-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e51ca-119">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e51ca-119">Compiling the code</span></span>  
  
- <span data-ttu-id="e51ca-120">O código usa os seguintes namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization> e <xref:System.Xml.Schema>.</span><span class="sxs-lookup"><span data-stu-id="e51ca-120">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e51ca-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e51ca-121">See also</span></span>

- [<span data-ttu-id="e51ca-122">Serialização personalizada</span><span class="sxs-lookup"><span data-stu-id="e51ca-122">Custom Serialization</span></span>](custom-serialization.md)
