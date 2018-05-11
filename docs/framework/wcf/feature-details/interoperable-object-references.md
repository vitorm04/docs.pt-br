---
title: Referências de objeto de interoperabilidade
ms.date: 03/30/2017
ms.assetid: cb8da4c8-08ca-4220-a16b-e04c8f527f1b
ms.openlocfilehash: eeedd39ec14a6758395aee1f4c3b8ab26a0c2ffd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="interoperable-object-references"></a><span data-ttu-id="74bfb-102">Referências de objeto de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="74bfb-102">Interoperable Object References</span></span>
<span data-ttu-id="74bfb-103">Por padrão o <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor.</span><span class="sxs-lookup"><span data-stu-id="74bfb-103">By default the <xref:System.Runtime.Serialization.DataContractSerializer> serializes objects by value.</span></span> <span data-ttu-id="74bfb-104">Você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriedade para instruir o serializador de contrato de dados para preservar as referências de objeto ao serializar objetos do tipo.</span><span class="sxs-lookup"><span data-stu-id="74bfb-104">You can use the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> property to instruct the Data Contract Serializer to preserve object references when serializing objects of the type.</span></span>  
  
## <a name="generated-xml"></a><span data-ttu-id="74bfb-105">XML gerado</span><span class="sxs-lookup"><span data-stu-id="74bfb-105">Generated XML</span></span>  
 <span data-ttu-id="74bfb-106">Por exemplo, considere o seguinte objeto:</span><span class="sxs-lookup"><span data-stu-id="74bfb-106">As an example, consider the following object:</span></span>  
  
```  
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
  
 <span data-ttu-id="74bfb-107">Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `false` (o padrão), o XML a seguir é gerado:</span><span class="sxs-lookup"><span data-stu-id="74bfb-107">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `false` (the default), the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 <span data-ttu-id="74bfb-108">Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definida como `true`, o XML a seguir é gerado:</span><span class="sxs-lookup"><span data-stu-id="74bfb-108">With <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> set to `true`, the following XML is generated:</span></span>  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1" />  
</X>  
```  
  
 <span data-ttu-id="74bfb-109">No entanto, <xref:System.Runtime.Serialization.XsdDataContractExporter> não descreve o `id` e `ref` atributos em seu esquema, mesmo quando o `preserveObjectReferences` está definida como `true`.</span><span class="sxs-lookup"><span data-stu-id="74bfb-109">However, <xref:System.Runtime.Serialization.XsdDataContractExporter> does not describe the `id` and `ref` attributes in its schema, even when the `preserveObjectReferences` property is set to `true`.</span></span>  
  
## <a name="using-isreference"></a><span data-ttu-id="74bfb-110">Usando IsReference</span><span class="sxs-lookup"><span data-stu-id="74bfb-110">Using IsReference</span></span>  
 <span data-ttu-id="74bfb-111">Para gerar informações de referência de objeto é válidas de acordo com o esquema que descreve a ele, aplicar o <xref:System.Runtime.Serialization.DataContractAttribute> para um tipo de atributo e definir o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> sinalizador como `true`.</span><span class="sxs-lookup"><span data-stu-id="74bfb-111">To generate object reference information that is valid according to the schema that describes it, apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to a type, and set the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> flag to `true`.</span></span> <span data-ttu-id="74bfb-112">Usando `IsReference` na classe do exemplo anterior `X`:</span><span class="sxs-lookup"><span data-stu-id="74bfb-112">Using `IsReference` in the previous example class `X`:</span></span>  
  
 `[DataContract(IsReference=true)] public class X`  
  
 `{`  
  
 `SomeClass someInstance = new SomeClass();`  
  
 `[DataMember]`  
  
 `public SomeClass A = someInstance;`  
  
 `[DataMember]`  
  
 `public SomeClass B = someInstance;`  
  
 `}`  
  
 `public class SomeClass`  
  
 `{`  
  
 `}`  
  
 <span data-ttu-id="74bfb-113">O XML gerado é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="74bfb-113">The generated XML is as follows:</span></span>  
  
 `<X>`  
  
 `<A id="1">`  
  
 `<Value>contents of A</Value>`  
  
 `</A>`  
  
 `<B ref="1">`  
  
 `</B>`  
  
 `</X>`  
  
 <span data-ttu-id="74bfb-114">Usando `IsReference` garante conformidade no ciclo de mensagem.</span><span class="sxs-lookup"><span data-stu-id="74bfb-114">Using `IsReference` ensures compliance on message round-tripping.</span></span> <span data-ttu-id="74bfb-115">Sem ele, quando um tipo é gerado do esquema, o que é enviado de volta como XML para que o tipo não é necessariamente compatível com o esquema originalmente assumido.</span><span class="sxs-lookup"><span data-stu-id="74bfb-115">Without it, when a type is generated from schema, what is sent back as XML for that type is not necessarily compatible with the schema originally assumed.</span></span> <span data-ttu-id="74bfb-116">Em outras palavras, embora o `id` e `ref` atributos foram serializados, o esquema original pode ter bloqueadas esses atributos (ou todos os atributos) ocorra no XML.</span><span class="sxs-lookup"><span data-stu-id="74bfb-116">In other words, although the `id` and `ref` attributes were serialized, the original schema could have barred these attributes (or all attributes) from occurring in the XML.</span></span> <span data-ttu-id="74bfb-117">Com `IsReference` aplicado a um membro de dados, o membro continua a ser reconhecido como "pode ser referenciado" quando roundtripped.</span><span class="sxs-lookup"><span data-stu-id="74bfb-117">With `IsReference` applied to a data member, the member continues to be recognized as "referenceable" when roundtripped.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74bfb-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74bfb-118">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference%2A>
