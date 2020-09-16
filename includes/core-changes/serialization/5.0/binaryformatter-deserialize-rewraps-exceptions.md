---
ms.openlocfilehash: 2e9267b35c9389da017927aca2346190348265c9
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87919377"
---
### <a name="binaryformatterdeserialize-rewraps-some-exceptions-in-serializationexception"></a><span data-ttu-id="60dab-101">BinaryFormatter. desserializate reencapsula algumas exceções na Serializaexception</span><span class="sxs-lookup"><span data-stu-id="60dab-101">BinaryFormatter.Deserialize rewraps some exceptions in SerializationException</span></span>

<span data-ttu-id="60dab-102">O <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> método agora reencapsula alguns objetos de exceção dentro de um <xref:System.Runtime.Serialization.SerializationException> antes de propagar a exceção de volta para o chamador.</span><span class="sxs-lookup"><span data-stu-id="60dab-102">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method now rewraps some exception objects inside a <xref:System.Runtime.Serialization.SerializationException> before propagating the exception back to the caller.</span></span>

#### <a name="change-description"></a><span data-ttu-id="60dab-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="60dab-103">Change description</span></span>

<span data-ttu-id="60dab-104">Anteriormente, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> método permitia algumas exceções arbitrárias, como <xref:System.ArgumentNullException> , para propagar a pilha para seus chamadores.</span><span class="sxs-lookup"><span data-stu-id="60dab-104">Previously, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method allowed some arbitrary exceptions, such as <xref:System.ArgumentNullException>, to propagate up the stack to its callers.</span></span>

<span data-ttu-id="60dab-105">No .NET 5,0 e posterior, o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> método captura de forma mais agressiva as exceções que ocorrem devido a operações de desserialização inválidas e as encapsula em um <xref:System.Runtime.Serialization.SerializationException> .</span><span class="sxs-lookup"><span data-stu-id="60dab-105">In .NET 5.0 and later, the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=nameWithType> method more aggressively catches exceptions that occur due to invalid deserialization operations and wraps them in a <xref:System.Runtime.Serialization.SerializationException>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="60dab-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="60dab-106">Version introduced</span></span>

<span data-ttu-id="60dab-107">5,0 visualização 1</span><span class="sxs-lookup"><span data-stu-id="60dab-107">5.0 Preview 1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="60dab-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="60dab-108">Recommended action</span></span>

<span data-ttu-id="60dab-109">Na maioria dos casos, você não precisa realizar nenhuma ação.</span><span class="sxs-lookup"><span data-stu-id="60dab-109">In most cases, you don't need to take any action.</span></span> <span data-ttu-id="60dab-110">No entanto, se seu site de chamada depende de uma determinada exceção sendo gerada, você pode desencapsular a exceção da externa <xref:System.Runtime.Serialization.SerializationException> , conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="60dab-110">However, if your call site depends on a particular exception being thrown, you can unwrap the exception from the outer <xref:System.Runtime.Serialization.SerializationException>, as shown in the following example.</span></span>

```csharp
Stream inputStream = GetInputStream();
var formatter = new BinaryFormatter();

try
{
    object deserialized = formatter.Deserialize(inputStream);
}
catch (MyException myEx)
{
    // Handle 'myEx' here in case it was thrown directly.
}
catch (SerializationException serEx) when (serEx.InnerException is MyException myEx)
{
    // Handle 'myEx' here in case it was wrapped in SerializationException.
}
```

#### <a name="category"></a><span data-ttu-id="60dab-111">Categoria</span><span class="sxs-lookup"><span data-stu-id="60dab-111">Category</span></span>

<span data-ttu-id="60dab-112">Serialização</span><span class="sxs-lookup"><span data-stu-id="60dab-112">Serialization</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="60dab-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="60dab-113">Affected APIs</span></span>

- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter.Deserialize`

-->
