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
# <a name="interoperable-object-references"></a>Referências de objeto interoperável
Por padrão, <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor. Você pode usar o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> propriedade para instruir o serializador de contrato de dados para preservar as referências de objeto ao serializar objetos.  
  
## <a name="generated-xml"></a>XML gerado  
 Por exemplo, considere o seguinte objeto:  
  
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
  
 Com o <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `false` (o padrão), o XML a seguir é gerado:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Com o <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido como `true`, o XML a seguir é gerado:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 No entanto, <xref:System.Runtime.Serialization.XsdDataContractExporter> não descreve o `id` e `ref` atributos no seu esquema, mesmo quando o `preserveObjectReferences` estiver definida como `true`.  
  
## <a name="using-isreference"></a>Usando IsReference  
 Para gerar informações de referência de objeto que é válidas de acordo com o esquema que descreve a ele, se aplicam a <xref:System.Runtime.Serialization.DataContractAttribute> a um tipo de atributo e, em seguida, defina a <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> sinalizador como `true`. O exemplo a seguir modifica a classe `X` no exemplo anterior, adicionando `IsReference`:  
  
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

 O XML gerado é da seguinte maneira:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A> 
    <B ref="1"></B>  
</X>
```  
  
 Usando `IsReference` garante a conformidade em um ciclo completo de mensagem. Sem ele, quando um tipo é gerado do esquema, o XML de saída para que o tipo não é necessariamente compatível com o esquema originalmente assumido. Em outras palavras, embora a `id` e `ref` atributos foram serializados, esquema original pode ter barrados esses atributos (ou todos os atributos) de ocorrendo no XML. Com o `IsReference` aplicado a um membro de dados, o membro continua a ser reconhecido como *referenciável* quando recuperado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
