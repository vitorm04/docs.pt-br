---
title: Controlando a serialização XML usando atributos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET Framework], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
ms.openlocfilehash: 54660244c1b3cca8cb75539edbe23628b370afd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54686160"
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="71b45-102">Controlando a serialização XML usando atributos</span><span class="sxs-lookup"><span data-stu-id="71b45-102">Controlling XML Serialization Using Attributes</span></span>

<span data-ttu-id="71b45-103">Os atributos podem ser usados para controlar a serialização XML de um objeto ou criar um fluxo XML alternativo do mesmo conjunto de classes.</span><span class="sxs-lookup"><span data-stu-id="71b45-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="71b45-104">Para obter mais detalhes sobre como criar um fluxo XML alternativo, consulte [como: Especifique um nome de elemento alternativo para um Stream do XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="71b45-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="71b45-105">Se o XML gerado deve estar em conformidade com a seção 5 do documento do World Wide Web Consortium (W3C) [simples objeto Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use os atributos listados em [atributos que controle codificado em SOAP Serialização](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="71b45-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="71b45-106">Por padrão, um nome de elemento XML é determinado pela classe ou nome do membro.</span><span class="sxs-lookup"><span data-stu-id="71b45-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="71b45-107">Em uma classe simples chamada `Book`, um campo chamado `ISBN` produzirá uma marcação de elemento XML \<ISBN>, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="71b45-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

```vb
Public Class Book
    Public ISBN As String
End Class
' When an instance of the Book class is serialized, it might
' produce this XML:
' <ISBN>1234567890</ISBN>.
```

```csharp
public class Book
{
    public string ISBN;
}
// When an instance of the Book class is serialized, it might
// produce this XML:
// <ISBN>1234567890</ISBN>.
```

<span data-ttu-id="71b45-108">Esse comportamento padrão pode ser modificado se você quiser dar ao elemento um novo nome.</span><span class="sxs-lookup"><span data-stu-id="71b45-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="71b45-109">O código a seguir mostra como um atributo permite isso definindo a propriedade <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> de um <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="71b45-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

<span data-ttu-id="71b45-110">Para obter mais informações sobre atributos, consulte [Atributos](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="71b45-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="71b45-111">Para obter uma lista de atributos que controlam a serialização XML, consulte [Atributos que controlam a serialização XML](attributes-that-control-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="71b45-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="71b45-112">Controlando a serialização de matriz</span><span class="sxs-lookup"><span data-stu-id="71b45-112">Controlling Array Serialization</span></span>

<span data-ttu-id="71b45-113">Os atributos <xref:System.Xml.Serialization.XmlArrayAttribute> e <xref:System.Xml.Serialization.XmlArrayItemAttribute> são criados para controlar a serialização de matrizes.</span><span class="sxs-lookup"><span data-stu-id="71b45-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="71b45-114">Usando esses atributos, você pode controlar o nome do elemento, namespace e tipo de dados XSD (esquema XML) (conforme definido no documento do World Wide Web Consortium [www.w3.org] intitulado "XML Schema Part 2: Tipos de dados").</span><span class="sxs-lookup"><span data-stu-id="71b45-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="71b45-115">Você também pode especificar os tipos que podem ser incluídos em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="71b45-115">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="71b45-116">O <xref:System.Xml.Serialization.XmlArrayAttribute> determinará as propriedades do elemento XML incluído que resulta quando uma matriz é serializada.</span><span class="sxs-lookup"><span data-stu-id="71b45-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="71b45-117">Por exemplo, por padrão, serializar a matriz abaixo resultará em um elemento XML denominado `Employees`.</span><span class="sxs-lookup"><span data-stu-id="71b45-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="71b45-118">O elemento `Employees` conterá uma série de elementos nomeados de acordo com o tipo de matriz `Employee`.</span><span class="sxs-lookup"><span data-stu-id="71b45-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

<span data-ttu-id="71b45-119">Uma instância serializada pode parecer com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="71b45-119">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="71b45-120">Aplicando um <xref:System.Xml.Serialization.XmlArrayAttribute>, você pode alterar o nome do elemento XML, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="71b45-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

<span data-ttu-id="71b45-121">O XML resultante pode parecer com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="71b45-121">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="71b45-122">O <xref:System.Xml.Serialization.XmlArrayItemAttribute>, por outro lado, controla como os itens contidos na matriz são serializados.</span><span class="sxs-lookup"><span data-stu-id="71b45-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="71b45-123">Observe que o atributo é aplicado ao campo que retorna a matriz.</span><span class="sxs-lookup"><span data-stu-id="71b45-123">Note that the attribute is applied to the field returning the array.</span></span>

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

<span data-ttu-id="71b45-124">O XML resultante pode parecer com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="71b45-124">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="71b45-125">Serializando classes derivadas</span><span class="sxs-lookup"><span data-stu-id="71b45-125">Serializing Derived Classes</span></span>

<span data-ttu-id="71b45-126">Outro uso do <xref:System.Xml.Serialization.XmlArrayItemAttribute> é permitir a serialização de classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="71b45-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="71b45-127">Por exemplo, outra classe denominada `Manager` que é derivada de `Employee` pode ser adicionada ao exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="71b45-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="71b45-128">Se você não aplicar o <xref:System.Xml.Serialization.XmlArrayItemAttribute>, o código falhará em tempo de execução porque o tipo da classe derivada não será reconhecido.</span><span class="sxs-lookup"><span data-stu-id="71b45-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="71b45-129">Para corrigir isso, aplique o atributo duas vezes, cada vez que definir a propriedade <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> para cada tipo aceitável (base e derivada).</span><span class="sxs-lookup"><span data-stu-id="71b45-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

```vb
Public Class Group
    <XmlArrayItem(Type:=GetType(Employee)), _
    XmlArrayItem(Type:=GetType(Manager))> _
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
Public Class Manager
Inherits Employee
    Public Level As Integer
End Class
```

```csharp
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

<span data-ttu-id="71b45-130">Uma instância serializada pode parecer com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="71b45-130">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    <Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="71b45-131">Serializando uma matriz como uma sequência de elementos</span><span class="sxs-lookup"><span data-stu-id="71b45-131">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="71b45-132">Você também pode serializar uma matriz como uma sequência plana dos elementos XML aplicando um <xref:System.Xml.Serialization.XmlElementAttribute> ao campo que retorna a matriz da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="71b45-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

<span data-ttu-id="71b45-133">Uma instância serializada pode parecer com o seguinte.</span><span class="sxs-lookup"><span data-stu-id="71b45-133">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Name>Haley</Name>
</Employees>
<Employees>
    <Name>Noriko</Name>
</Employees>
<Employees>
    <Name>Marco</Name>
</Employees>
</Group>
```

<span data-ttu-id="71b45-134">Outra maneira para diferenciar os dois fluxos XML é usar a Ferramenta de Definição de Esquema XML para gerar os arquivos de documento de esquema XSD de código compilado.</span><span class="sxs-lookup"><span data-stu-id="71b45-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="71b45-135">(Para obter mais detalhes sobre como usar a ferramenta, consulte [A ferramenta de definição de esquema XML e a serialização XML](the-xml-schema-definition-tool-and-xml-serialization.md).) Quando nenhum atributo é aplicado ao campo, o esquema descreve o elemento da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="71b45-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="71b45-136">Quando o <xref:System.Xml.Serialization.XmlElementAttribute> é aplicado ao campo, o esquema resultante descreve o elemento da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="71b45-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" /> 
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="71b45-137">Serializando um ArrayList</span><span class="sxs-lookup"><span data-stu-id="71b45-137">Serializing an ArrayList</span></span>

<span data-ttu-id="71b45-138">A classe <xref:System.Collections.ArrayList> pode conter uma coleção de vários objetos.</span><span class="sxs-lookup"><span data-stu-id="71b45-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="71b45-139">Você pode, portanto, usar um <xref:System.Collections.ArrayList> da mesma maneira que usa uma matriz.</span><span class="sxs-lookup"><span data-stu-id="71b45-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="71b45-140">Em vez de criar um campo que retorna uma matriz de objetos tipados, no entanto, você pode criar um campo que retorna um único <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="71b45-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="71b45-141">No entanto, da mesma forma que ocorre com matrizes, você deverá informar o <xref:System.Xml.Serialization.XmlSerializer> dos tipos de objetos que o <xref:System.Collections.ArrayList> contém.</span><span class="sxs-lookup"><span data-stu-id="71b45-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="71b45-142">Para fazer isso, atribua várias instâncias do <xref:System.Xml.Serialization.XmlElementAttribute> ao campo, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="71b45-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)), 
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="71b45-143">Controlando a serialização de classes usando XmlRootAttribute e XmlTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="71b45-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="71b45-144">Há dois atributos que podem ser aplicados a uma classe (e somente a uma classe): <xref:System.Xml.Serialization.XmlRootAttribute> e <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="71b45-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="71b45-145">Esses atributos são muito semelhantes.</span><span class="sxs-lookup"><span data-stu-id="71b45-145">These attributes are very similar.</span></span> <span data-ttu-id="71b45-146">O <xref:System.Xml.Serialization.XmlRootAttribute> pode ser aplicado somente a uma classe: a classe que, quando serializada, representa o elemento de abertura e fechamento do documento XML. Em outras palavras, o elemento raiz.</span><span class="sxs-lookup"><span data-stu-id="71b45-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="71b45-147">O <xref:System.Xml.Serialization.XmlTypeAttribute>, por outro lado, pode ser aplicado a qualquer classe, incluindo a classe raiz.</span><span class="sxs-lookup"><span data-stu-id="71b45-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="71b45-148">Por exemplo, nos exemplos anteriores, a classe `Group` é a classe raiz, e todos os seus campos públicos e propriedades tornam-se elementos XML encontrados no documento XML.</span><span class="sxs-lookup"><span data-stu-id="71b45-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="71b45-149">Portanto, pode haver apenas uma classe de raiz.</span><span class="sxs-lookup"><span data-stu-id="71b45-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="71b45-150">Aplicando o <xref:System.Xml.Serialization.XmlRootAttribute>, você pode controlar o fluxo XML produzido pelo <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="71b45-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="71b45-151">Por exemplo, você pode alterar o nome e o namespace do elemento.</span><span class="sxs-lookup"><span data-stu-id="71b45-151">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="71b45-152">O <xref:System.Xml.Serialization.XmlTypeAttribute> permite que você controle o esquema do XML gerado.</span><span class="sxs-lookup"><span data-stu-id="71b45-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="71b45-153">Esse recurso é útil quando você precisa publicar o esquema por um serviço Web XML.</span><span class="sxs-lookup"><span data-stu-id="71b45-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="71b45-154">O exemplo a seguir aplica o <xref:System.Xml.Serialization.XmlTypeAttribute> e o <xref:System.Xml.Serialization.XmlRootAttribute> à mesma classe.</span><span class="sxs-lookup"><span data-stu-id="71b45-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

```vb
<XmlRoot("NewGroupName"), _
XmlType("NewTypeName")> _
Public Class Group
    Public Employees() As Employee
End Class
```

```csharp
[XmlRoot("NewGroupName")]
[XmlType("NewTypeName")]
public class Group {
    public Employee[] Employees;
}
```

<span data-ttu-id="71b45-155">Se essa classe for criada, e a ferramenta de Definição de Esquema XML for usada para gerar seu esquema, você descobriria o seguinte XML descrevendo o `Group`.</span><span class="sxs-lookup"><span data-stu-id="71b45-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName">
```

<span data-ttu-id="71b45-156">Por outro lado, se você quisesse serializar uma instância da classe, somente `NewGroupName` seria encontrado no documento XML.</span><span class="sxs-lookup"><span data-stu-id="71b45-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="71b45-157">Evitando a serialização com o XmlIgnoreAttribute</span><span class="sxs-lookup"><span data-stu-id="71b45-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="71b45-158">Pode haver situações quando uma propriedade pública ou um campo não precisam ser serializados.</span><span class="sxs-lookup"><span data-stu-id="71b45-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="71b45-159">Por exemplo, um campo ou propriedade podem ser usados para conter metadados.</span><span class="sxs-lookup"><span data-stu-id="71b45-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="71b45-160">Nesses casos, aplicar o <xref:System.Xml.Serialization.XmlIgnoreAttribute> ao campo ou propriedade e o <xref:System.Xml.Serialization.XmlSerializer> o ignorarão.</span><span class="sxs-lookup"><span data-stu-id="71b45-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="71b45-161">Consulte também</span><span class="sxs-lookup"><span data-stu-id="71b45-161">See also</span></span>

- [<span data-ttu-id="71b45-162">Atributos que controlam a serialização XML</span><span class="sxs-lookup"><span data-stu-id="71b45-162">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="71b45-163">Atributos que controlam a serialização SOAP codificada</span><span class="sxs-lookup"><span data-stu-id="71b45-163">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="71b45-164">Apresentando a serialização XML</span><span class="sxs-lookup"><span data-stu-id="71b45-164">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="71b45-165">Exemplos de serialização XML</span><span class="sxs-lookup"><span data-stu-id="71b45-165">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)
- [<span data-ttu-id="71b45-166">Como: Especifique um nome de elemento alternativo para um Stream XML</span><span class="sxs-lookup"><span data-stu-id="71b45-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="71b45-167">Como: Serializar um objeto</span><span class="sxs-lookup"><span data-stu-id="71b45-167">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="71b45-168">Como: Desserializar um objeto</span><span class="sxs-lookup"><span data-stu-id="71b45-168">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
