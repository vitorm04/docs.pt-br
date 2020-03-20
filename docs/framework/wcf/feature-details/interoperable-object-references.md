---
title: Referências de objetos interoperáveis
ms.date: 04/15/2019
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: 0927f217a1666f8f27ca9c3e68f80a96b9c0f2b1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184700"
---
# <a name="interoperable-object-references"></a><span data-ttu-id="50f02-102">Referências de objetos interoperáveis</span><span class="sxs-lookup"><span data-stu-id="50f02-102">Interoperable object references</span></span>
<span data-ttu-id="50f02-103">Por padrão, <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor.</span><span class="sxs-lookup"><span data-stu-id="50f02-103">By default, <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="50f02-104">Você pode <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> usar a propriedade para instruir o serializador de contratos de dados para preservar referências de objetos ao serializar objetos.</span><span class="sxs-lookup"><span data-stu-id="50f02-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the data contract serializer to preserve object references when serializing objects.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="50f02-105">XML gerado</span><span class="sxs-lookup"><span data-stu-id="50f02-105">Generated XML</span></span>  
 <span data-ttu-id="50f02-106">Como exemplo, considere o seguinte objeto:</span><span class="sxs-lookup"><span data-stu-id="50f02-106">As an example, consider the following object:</span></span>  
  
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
  
 <span data-ttu-id="50f02-107">Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido `false` como (o padrão), o Seguinte XML é gerado:</span><span class="sxs-lookup"><span data-stu-id="50f02-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="50f02-108">Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido `true`para , o seguinte XML é gerado:</span><span class="sxs-lookup"><span data-stu-id="50f02-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 <span data-ttu-id="50f02-109">No <xref:System.Runtime.Serialization.XsdDataContractExporter> entanto, não `id` `ref` descreve os e atributos em `preserveObjectReferences` seu esquema, mesmo quando a propriedade é definida para `true`.</span><span class="sxs-lookup"><span data-stu-id="50f02-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> doesn't describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="50f02-110">Usando isreference</span><span class="sxs-lookup"><span data-stu-id="50f02-110">Using IsReference</span></span>  
 <span data-ttu-id="50f02-111">Para gerar informações de referência de objeto válidas de acordo com <xref:System.Runtime.Serialization.DataContractAttribute> o esquema que a <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> descreve, aplique o atributo a um tipo e defina a bandeira para `true`.</span><span class="sxs-lookup"><span data-stu-id="50f02-111">To generate object reference information that's valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="50f02-112">O exemplo a `X` seguir modifica a `IsReference`classe no exemplo anterior adicionando:</span><span class="sxs-lookup"><span data-stu-id="50f02-112">The following example modifies class `X` in the previous example by adding `IsReference`:</span></span>  
  
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

 <span data-ttu-id="50f02-113">O XML gerado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="50f02-113">The generated XML is as follows:</span></span>  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 <span data-ttu-id="50f02-114">O `IsReference` uso garante a conformidade em tropeços redondos de mensagens.</span><span class="sxs-lookup"><span data-stu-id="50f02-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="50f02-115">Sem ele, quando um tipo é gerado a partir de esquema, a saída XML para esse tipo não é necessariamente compatível com o esquema originalmente assumido.</span><span class="sxs-lookup"><span data-stu-id="50f02-115">Without it, when a type is generated from schema, the XML output for that type isn't necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="50f02-116">Em outras palavras, `ref` embora os atributos e atributos `id` tenham sido serializados, o esquema original poderia ter impedido esses atributos (ou todos os atributos) de ocorrer no XML.</span><span class="sxs-lookup"><span data-stu-id="50f02-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="50f02-117">Com `IsReference` a aplicação a um membro de dados, o membro continua a ser reconhecido como *referencial* quando tropeçado.</span><span class="sxs-lookup"><span data-stu-id="50f02-117">With `IsReference` applied to a data member, the member continues to be recognized as *referenceable* when round-tripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50f02-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="50f02-118">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
