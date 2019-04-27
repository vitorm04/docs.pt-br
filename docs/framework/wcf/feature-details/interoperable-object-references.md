---
title: Referências de objeto interoperável
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: ada9084f6ac3c97dc641571c0cb8379a2fac68a8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61918964"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="520f2-102">Referências de objeto interoperável</span><span class="sxs-lookup"><span data-stu-id="520f2-102">Interoperable object references</span></span>
<span data-ttu-id="520f2-103">Por padrão, <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor.</span><span class="sxs-lookup"><span data-stu-id="520f2-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="520f2-104">Você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriedade para instruir o serializador de contrato de dados para preservar as referências de objeto ao serializar objetos.</span><span class="sxs-lookup"><span data-stu-id="520f2-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="520f2-105">XML gerado</span><span class="sxs-lookup"><span data-stu-id="520f2-105">Generated XML</span></span>  
 <span data-ttu-id="520f2-106">Por exemplo, considere o seguinte objeto:</span><span class="sxs-lookup"><span data-stu-id="520f2-106">As an example, consider the following object:</span></span>  
  
```csharp  
[DataContract]  
public class X  
{  
    SomeClass someInstance = new SomeClass();  
    [DataMember]  
    public SomeClass A = someInstance;  
    [DataMember]  
    public SomeClass B = someInstance;  
}  
  
public class SomeClass   
{  
}  
```  
  
 <span data-ttu-id="520f2-107">Com o <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `false` (o padrão), o XML a seguir é gerado:</span><span class="sxs-lookup"><span data-stu-id="520f2-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="520f2-108">Com o <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `true`, o XML a seguir é gerado:</span><span class="sxs-lookup"><span data-stu-id="520f2-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="520f2-109">No entanto, <xref:System.Runtime.Serialization.XsdDataContractExporter> não descreve o `id` e `ref` atributos no seu esquema, mesmo quando o `preserveObjectReferences` estiver definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="520f2-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="520f2-110">Usando IsReference</span><span class="sxs-lookup"><span data-stu-id="520f2-110">Using IsReference</span></span>  
 <span data-ttu-id="520f2-111">Para gerar informações de referência de objeto que é válidas de acordo com o esquema que descreve a ele, se aplicam a <xref:System.Runtime.Serialization.DataContractAttribute> a um tipo de atributo e, em seguida, defina a <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> sinalizador como `true`.</span><span class="sxs-lookup"><span data-stu-id="520f2-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="520f2-112">O exemplo a seguir modifica a classe `X` no exemplo anterior, adicionando `IsReference`:</span><span class="sxs-lookup"><span data-stu-id="520f2-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
```csharp
[DataContract(IsReference=true)]
public class X   
{  
     SomeClass someInstance = new SomeClass(); 
     [DataMember]
     public SomeClass A = someInstance;
     [DataMember] 
     public SomeClass B = someInstance;
}
  
public class SomeClass 
{   
}  
````

 <span data-ttu-id="520f2-113">O XML gerado é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="520f2-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="520f2-114">Usando `IsReference` garante a conformidade em um ciclo completo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="520f2-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="520f2-115">Sem ele, quando um tipo é gerado do esquema, o XML de saída para que o tipo não é necessariamente compatível com o esquema originalmente assumido.</span><span class="sxs-lookup"><span data-stu-id="520f2-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="520f2-116">Em outras palavras, embora a `id` e `ref` atributos foram serializados, esquema original pode ter barrados esses atributos (ou todos os atributos) de ocorrendo no XML.</span><span class="sxs-lookup"><span data-stu-id="520f2-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="520f2-117">Com o `IsReference` aplicado a um membro de dados, o membro continua a ser reconhecido como *referenciável* quando recuperado.</span><span class="sxs-lookup"><span data-stu-id="520f2-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="520f2-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="520f2-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
