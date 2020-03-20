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
# <a name="interoperable-object-references"></a>Referências de objetos interoperáveis
Por padrão, <xref:System.Runtime.Serialization.DataContractSerializer> serializa objetos por valor. Você pode <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> usar a propriedade para instruir o serializador de contratos de dados para preservar referências de objetos ao serializar objetos.  
  
## <a name="generated-xml"></a>XML gerado  
 Como exemplo, considere o seguinte objeto:  
  
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
  
 Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido `false` como (o padrão), o Seguinte XML é gerado:  
  
```xml  
<X>  
   <A>contents of someInstance</A>  
   <B>contents of someInstance</B>  
</X>  
```  
  
 Com <xref:System.Runtime.Serialization.DataContractSerializer.PreserveObjectReferences%2A> definido `true`para , o seguinte XML é gerado:  
  
```xml  
<X>  
   <A id="1">contents of someInstance</A>  
   <B ref="1"></B>  
</X>  
```  
  
 No <xref:System.Runtime.Serialization.XsdDataContractExporter> entanto, não `id` `ref` descreve os e atributos em `preserveObjectReferences` seu esquema, mesmo quando a propriedade é definida para `true`.  
  
## <a name="using-isreference"></a>Usando isreference  
 Para gerar informações de referência de objeto válidas de acordo com <xref:System.Runtime.Serialization.DataContractAttribute> o esquema que a <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> descreve, aplique o atributo a um tipo e defina a bandeira para `true`. O exemplo a `X` seguir modifica a `IsReference`classe no exemplo anterior adicionando:  
  
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

 O XML gerado é o seguinte:  

```xml
<X>  
    <A id="1">
        <Value>contents of A</Value>  
    </A>
    <B ref="1"></B>  
</X>
```  
  
 O `IsReference` uso garante a conformidade em tropeços redondos de mensagens. Sem ele, quando um tipo é gerado a partir de esquema, a saída XML para esse tipo não é necessariamente compatível com o esquema originalmente assumido. Em outras palavras, `ref` embora os atributos e atributos `id` tenham sido serializados, o esquema original poderia ter impedido esses atributos (ou todos os atributos) de ocorrer no XML. Com `IsReference` a aplicação a um membro de dados, o membro continua a ser reconhecido como *referencial* quando tropeçado.  
  
## <a name="see-also"></a>Confira também

- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference?displayProperty=nameWithType>
- <xref:System.Runtime.Serialization.CollectionDataContractAttribute.IsReference?displayProperty=nameWithType>
