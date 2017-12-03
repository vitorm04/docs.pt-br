---
title: "Comparando os serviços Web ASP.NET com o WCF baseado em desenvolvimento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f362d00e-ce82-484f-9d4f-27e579d5c320
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6aa79e76bd81c0d56b30d4bac2edd4b9cbef6b33
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-aspnet-web-services-to-wcf-based-on-development"></a><span data-ttu-id="908aa-102">Comparando os serviços Web ASP.NET com o WCF baseado em desenvolvimento</span><span class="sxs-lookup"><span data-stu-id="908aa-102">Comparing ASP.NET Web Services to WCF Based on Development</span></span>
<span data-ttu-id="908aa-103">O [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tem uma opção de modo de compatibilidade com o ASP.NET que permite que os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sejam programados e configurados como serviços Web ASP.NET, e simulam seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="908aa-103">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] has an ASP.NET compatibility mode option to enable [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications to be programmed and configured like ASP.NET Web services, and mimic their behavior.</span></span> <span data-ttu-id="908aa-104">As seções a seguir comparam os serviços Web ASP.NET e o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com base no que é necessário para desenvolver aplicativos usando as duas tecnologias.</span><span class="sxs-lookup"><span data-stu-id="908aa-104">The following sections compare ASP.NET Web services and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] based on what is required to develop applications using both technologies.</span></span>  
  
## <a name="data-representation"></a><span data-ttu-id="908aa-105">Representação de dados</span><span class="sxs-lookup"><span data-stu-id="908aa-105">Data Representation</span></span>  
 <span data-ttu-id="908aa-106">O desenvolvimento de um serviço Web com o ASP.NET geralmente começa com a definição de quaisquer tipos de dados complexos que o serviço usará.</span><span class="sxs-lookup"><span data-stu-id="908aa-106">The development of a Web service with ASP.NET typically begins with defining any complex data types the service is to use.</span></span> <span data-ttu-id="908aa-107">O ASP.NET conta com o <xref:System.Xml.Serialization.XmlSerializer> para converter os dados representados por tipos do .NET Framework em XML para transmissão para ou de um serviço e para converter os dados recebidos como XML em objetos do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="908aa-107">ASP.NET relies on the <xref:System.Xml.Serialization.XmlSerializer> to translate data represented by .NET Framework types to XML for transmission to or from a service and to translate data received as XML into .NET Framework objects.</span></span> <span data-ttu-id="908aa-108">Definir os tipos de dados complexos que um serviço do ASP.NET usará requer a definição das classes do .NET Framework que o <xref:System.Xml.Serialization.XmlSerializer> pode serializar para e do XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-108">Defining the complex data types that an ASP.NET service is to use requires the definition of .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML.</span></span> <span data-ttu-id="908aa-109">Essas classes podem ser gravadas manualmente, ou geradas a partir das definições dos tipos no Esquema XML usando o utilitário de linha de comando para suporte de tipos de dados/esquemas XML, o xsd.exe.</span><span class="sxs-lookup"><span data-stu-id="908aa-109">Such classes can be written manually, or generated from definitions of the types in XML Schema using the command-line XML Schemas/Data Types Support Utility, xsd.exe.</span></span>  
  
 <span data-ttu-id="908aa-110">Esta é uma lista dos principais problemas que precisam ser conhecidos ao definir as classes do .NET Framework que o <xref:System.Xml.Serialization.XmlSerializer> pode serializar para e do XML:</span><span class="sxs-lookup"><span data-stu-id="908aa-110">The following is a list of key issues to know when defining .NET Framework classes that the <xref:System.Xml.Serialization.XmlSerializer> can serialize to and from XML:</span></span>  
  
-   <span data-ttu-id="908aa-111">Somente as propriedades e os campos públicos dos objetos do .NET Framework são convertidos em XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-111">Only the public fields and properties of .NET Framework objects are translated into XML.</span></span>  
  
-   <span data-ttu-id="908aa-112">As instâncias de classes de coleção poderão ser serializadas em XML somente se as classes implementarem a interface <xref:System.Collections.IEnumerable> ou <xref:System.Collections.ICollection>.</span><span class="sxs-lookup"><span data-stu-id="908aa-112">Instances of collection classes can be serialized into XML only if the classes implement either the <xref:System.Collections.IEnumerable> or <xref:System.Collections.ICollection> interface.</span></span>  
  
-   <span data-ttu-id="908aa-113">As classes que implementam a interface <xref:System.Collections.IDictionary>, como <xref:System.Collections.Hashtable>, não podem ser serializadas em XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-113">Classes that implement the <xref:System.Collections.IDictionary> interface, such as <xref:System.Collections.Hashtable>, cannot be serialized into XML.</span></span>  
  
-   <span data-ttu-id="908aa-114">A maioria dos tipos de atributo do namespace <xref:System.Xml.Serialization> pode ser adicionada a uma classe do .NET Framework e a seus membros para controlar como as instâncias da classe serão representadas em XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-114">The great many attribute types in the <xref:System.Xml.Serialization> namespace can be added to a .NET Framework class and its members to control how instances of the class are represented in XML.</span></span>  
  
 <span data-ttu-id="908aa-115">O desenvolvimento de aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] normalmente também começa com a definição de tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="908aa-115">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application development usually also begins with the definition of complex types.</span></span> <span data-ttu-id="908aa-116">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode ser desenvolvido de modo a usar os mesmos tipos do .NET Framework que os serviços Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-116">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can be made to use the same .NET Framework types as ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="908aa-117">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e o <xref:System.Runtime.Serialization.DataContractAttribute> do <xref:System.Runtime.Serialization.DataMemberAttribute> podem ser adicionados aos tipos do .NET Framework para indicar que as instâncias do tipo serão serializadas em XML, e quais campos ou propriedades específicos do tipo serão serializados, conforme mostrado no código de exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="908aa-117">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> can be added to .NET Framework types to indicate that instances of the type are to be serialized into XML, and which particular fields or properties of the type are to be serialized, as shown in the following sample code.</span></span>  
  
```  
//Example One:   
[DataContract]  
public class LineItem  
{  
    [DataMember]  
    public string ItemNumber;  
    [DataMember]  
    public decimal Quantity;  
    [DataMember]  
    public decimal UnitPrice;  
}  
  
//Example Two:   
public class LineItem  
{  
    [DataMember]  
    private string itemNumber;  
    [DataMember]  
    private decimal quantity;  
    [DataMember]  
    private decimal unitPrice;  
  
    public string ItemNumber  
    {  
      get  
      {  
          return this.itemNumber;  
      }  
  
      set  
      {  
          this.itemNumber = value;  
      }  
    }  
  
    public decimal Quantity  
    {  
        get  
        {  
            return this.quantity;  
        }  
  
        set  
        {  
            this.quantity = value;  
        }  
    }  
  
    public decimal UnitPrice  
    {  
      get  
      {  
          return this.unitPrice;  
      }  
  
      set  
      {  
          this.unitPrice = value;  
      }  
    }  
}  
  
//Example Three:   
public class LineItem  
{  
     private string itemNumber;  
     private decimal quantity;  
     private decimal unitPrice;  
  
     [DataMember]  
     public string ItemNumber  
     {  
       get  
       {  
          return this.itemNumber;  
       }  
  
       set  
       {  
           this.itemNumber = value;  
       }  
     }  
  
     [DataMember]  
     public decimal Quantity  
     {  
          get  
          {  
              return this.quantity;  
          }  
  
          set  
          {  
             this.quantity = value;  
          }  
     }  
  
     [DataMember]  
     public decimal UnitPrice  
     {  
          get  
          {  
              return this.unitPrice;  
          }  
  
          set  
          {  
              this.unitPrice = value;  
          }  
     }  
}  
```  
  
 <span data-ttu-id="908aa-118">O <xref:System.Runtime.Serialization.DataContractAttribute> significa que zero ou mais campos ou propriedades de um tipo serão serializados, enquanto <xref:System.Runtime.Serialization.DataMemberAttribute> indica que um campo ou propriedade serão serializados.</span><span class="sxs-lookup"><span data-stu-id="908aa-118">The <xref:System.Runtime.Serialization.DataContractAttribute> signifies that zero or more of a type’s fields or properties are to be serialized, while the <xref:System.Runtime.Serialization.DataMemberAttribute> indicates that a particular field or property is to be serialized.</span></span> <span data-ttu-id="908aa-119">O <xref:System.Runtime.Serialization.DataContractAttribute> pode ser aplicado a uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="908aa-119">The <xref:System.Runtime.Serialization.DataContractAttribute> can be applied to a class or structure.</span></span> <span data-ttu-id="908aa-120">O <xref:System.Runtime.Serialization.DataMemberAttribute> pode ser aplicado a um campo ou uma propriedade, e os campos e as propriedades aos quais o atributo é aplicado podem ser públicos ou privados.</span><span class="sxs-lookup"><span data-stu-id="908aa-120">The <xref:System.Runtime.Serialization.DataMemberAttribute> can be applied to a field or a property, and the fields and properties to which the attribute is applied can be either public or private.</span></span> <span data-ttu-id="908aa-121">As instâncias de tipos que têm o <xref:System.Runtime.Serialization.DataContractAttribute> aplicado a elas são chamadas de contratos de dados no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-121">Instances of types that have the <xref:System.Runtime.Serialization.DataContractAttribute> applied to them are referred to as data contracts in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="908aa-122">Elas são serializadas em XML por meio do <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="908aa-122">They are serialized into XML using <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
 <span data-ttu-id="908aa-123">Esta é uma lista das diferenças importantes entre o uso do <xref:System.Runtime.Serialization.DataContractSerializer> e do <xref:System.Xml.Serialization.XmlSerializer> e os vários atributos do namespace <xref:System.Xml.Serialization>.</span><span class="sxs-lookup"><span data-stu-id="908aa-123">The following is a list of the important differences between using the <xref:System.Runtime.Serialization.DataContractSerializer> and using the <xref:System.Xml.Serialization.XmlSerializer> and the various attributes of the <xref:System.Xml.Serialization> namespace.</span></span>  
  
-   <span data-ttu-id="908aa-124">O <xref:System.Xml.Serialization.XmlSerializer> e os atributos do namespace <xref:System.Xml.Serialization> são projetados para permitir que você mapeie os tipos do .NET Framework para qualquer tipo válido definido no Esquema XML e, portanto, oferecem um controle muito preciso sobre como um tipo é representado em XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-124">The <xref:System.Xml.Serialization.XmlSerializer> and the attributes of the <xref:System.Xml.Serialization> namespace are designed to allow you to map .NET Framework types to any valid type defined in XML Schema, and so they provide for very precise control over how a type is represented in XML.</span></span> <span data-ttu-id="908aa-125">O <xref:System.Runtime.Serialization.DataContractSerializer>, o <xref:System.Runtime.Serialization.DataContractAttribute> e o <xref:System.Runtime.Serialization.DataMemberAttribute> fornecem muito pouco controle sobre como um tipo é representado em XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-125">The <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.DataContractAttribute> and <xref:System.Runtime.Serialization.DataMemberAttribute> provide very little control over how a type is represented in XML.</span></span> <span data-ttu-id="908aa-126">Você pode especificar somente os namespaces e os nomes usados para representar o tipo e seus campos ou propriedades em XML, e a sequência na qual os campos e as propriedades aparecerão em XML:</span><span class="sxs-lookup"><span data-stu-id="908aa-126">You can only specify the namespaces and names used to represent the type and its fields or properties in the XML, and the sequence in which the fields and properties appear in the XML:</span></span>  
  
    ```  
    [DataContract(  
    Namespace="urn:Contoso:2006:January:29",  
    Name="LineItem")]  
    public class LineItem  
    {  
         [DataMember(Name="ItemNumber",IsRequired=true,Order=0)]  
         public string itemNumber;  
         [DataMember(Name="Quantity",IsRequired=false,Order = 1)]  
         public decimal quantity;  
         [DataMember(Name="Price",IsRequired=false,Order = 2)]  
         public decimal unitPrice;  
    }  
    ```  
  
     <span data-ttu-id="908aa-127">Tudo o mais sobre a estrutura do XML usado para representar o tipo do .NET é determinado pelo <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="908aa-127">Everything else about the structure of the XML used to represent the .NET type is determined by the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  
  
-   <span data-ttu-id="908aa-128">Não permitindo muito controle sobre como um tipo será representado em XML, o processo de serialização fica altamente previsível para o <xref:System.Runtime.Serialization.DataContractSerializer> e, assim, mais fácil para otimizar.</span><span class="sxs-lookup"><span data-stu-id="908aa-128">By not permitting much control over how a type is to be represented in XML, the serialization process becomes highly predictable for the <xref:System.Runtime.Serialization.DataContractSerializer>, and, thereby, easier to optimize.</span></span> <span data-ttu-id="908aa-129">Um benefício prático do design do <xref:System.Runtime.Serialization.DataContractSerializer> é o melhor desempenho, uma melhora de aproximadamente 10% no desempenho.</span><span class="sxs-lookup"><span data-stu-id="908aa-129">A practical benefit of the design of the <xref:System.Runtime.Serialization.DataContractSerializer> is better performance, approximately ten percent better performance.</span></span>  
  
-   <span data-ttu-id="908aa-130">Os atributos para uso com o <xref:System.Xml.Serialization.XmlSerializer> não indicam quais campos ou propriedades do tipo são serializados em XML, enquanto o <xref:System.Runtime.Serialization.DataMemberAttribute> para uso com o <xref:System.Runtime.Serialization.DataContractSerializer> mostra explicitamente quais campos ou propriedades são serializados.</span><span class="sxs-lookup"><span data-stu-id="908aa-130">The attributes for use with the <xref:System.Xml.Serialization.XmlSerializer> do not indicate which fields or properties of the type are serialized into XML, whereas the <xref:System.Runtime.Serialization.DataMemberAttribute> for use with the <xref:System.Runtime.Serialization.DataContractSerializer> shows explicitly which fields or properties are serialized.</span></span> <span data-ttu-id="908aa-131">Portanto, os contratos de dados são contratos explícitos sobre a estrutura dos dados que um aplicativo enviará e receberá.</span><span class="sxs-lookup"><span data-stu-id="908aa-131">Therefore, data contracts are explicit contracts about the structure of the data that an application is to send and receive.</span></span>  
  
-   <span data-ttu-id="908aa-132">O <xref:System.Xml.Serialization.XmlSerializer> só pode converter os membros públicos de um objeto .NET em XML, já o <xref:System.Runtime.Serialization.DataContractSerializer> pode converter os membros dos objetos em XML independentemente dos modificadores de acesso desses membros.</span><span class="sxs-lookup"><span data-stu-id="908aa-132">The <xref:System.Xml.Serialization.XmlSerializer> can only translate the public members of a .NET object into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> can translate the members of objects into XML regardless of the access modifiers of those members.</span></span>  
  
-   <span data-ttu-id="908aa-133">Como resultado da capacidade de serializar os membros não públicos dos tipos em XML, o <xref:System.Runtime.Serialization.DataContractSerializer> tem menos restrições no tocante aos vários tipos .NET que ele pode serializar em XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-133">As a consequence of being able to serialize the non-public members of types into XML, the <xref:System.Runtime.Serialization.DataContractSerializer> has fewer restrictions on the variety of .NET types that it can serialize into XML.</span></span> <span data-ttu-id="908aa-134">Especificamente, ele pode fazer a conversão em tipos XML como o <xref:System.Collections.Hashtable> que implementam a interface <xref:System.Collections.IDictionary>.</span><span class="sxs-lookup"><span data-stu-id="908aa-134">In particular, it can translate into XML types like <xref:System.Collections.Hashtable> that implement the <xref:System.Collections.IDictionary> interface.</span></span> <span data-ttu-id="908aa-135">O <xref:System.Runtime.Serialization.DataContractSerializer> tem muito mais probabilidade de poder serializar as instâncias de qualquer tipo .NET pré-existente em XML sem precisar modificar a definição do tipo ou desenvolver um wrapper para ele.</span><span class="sxs-lookup"><span data-stu-id="908aa-135">The <xref:System.Runtime.Serialization.DataContractSerializer> is much more likely to be able to serialize the instances of any pre-existing .NET type into XML without having to either modify the definition of the type or develop a wrapper for it.</span></span>  
  
-   <span data-ttu-id="908aa-136">Outra consequência da capacidade do <xref:System.Runtime.Serialization.DataContractSerializer> de acessar os membros não públicos de um tipo é que ele requer confiança total, enquanto o <xref:System.Xml.Serialization.XmlSerializer> não.</span><span class="sxs-lookup"><span data-stu-id="908aa-136">Another consequence of the <xref:System.Runtime.Serialization.DataContractSerializer> being able to access the non-public members of a type is that it requires full trust, whereas the <xref:System.Xml.Serialization.XmlSerializer> does not.</span></span> <span data-ttu-id="908aa-137">A permissão de acesso de código Confiança Total fornece acesso completo a todos os recursos em um computador que pode ser acessado por meio das credenciais na qual o código está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="908aa-137">The Full Trust code access permission give complete access to all resources on a machine that can be access using the credentials under which the code is executing.</span></span> <span data-ttu-id="908aa-138">Essas opções devem ser usadas com cuidado, pois o código totalmente confiável acessa todos os recursos do computador.</span><span class="sxs-lookup"><span data-stu-id="908aa-138">This options should be used with care as fully trusted code accesses all resources on your machine.</span></span>  
  
-   <span data-ttu-id="908aa-139">O <xref:System.Runtime.Serialization.DataContractSerializer> oferece algum suporte para controle de versão:</span><span class="sxs-lookup"><span data-stu-id="908aa-139">The <xref:System.Runtime.Serialization.DataContractSerializer> incorporates some support for versioning:</span></span>  
  
    -   <span data-ttu-id="908aa-140">O <xref:System.Runtime.Serialization.DataMemberAttribute> tem uma propriedade <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> que pode receber um valor false para membros adicionados às novas versões de um contrato de dados que não estavam presentes nas versões anteriores, permitindo assim que aplicativos com a versão mais recente do contrato possam processar versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="908aa-140">The <xref:System.Runtime.Serialization.DataMemberAttribute> has an <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> property that can be assigned a value of false for members that are added to new versions of a data contract that were not present in earlier versions, thereby allowing applications with the newer version of the contract to be able to process earlier versions.</span></span>  
  
    -   <span data-ttu-id="908aa-141">Tendo um contrato de dados que implemente a interface <xref:System.Runtime.Serialization.IExtensibleDataObject>, uma pessoa pode permitir que o <xref:System.Runtime.Serialization.DataContractSerializer> passe os membros definidos nas versões mais recentes de um contrato de dados por meio de aplicativos com versões anteriores do contrato.</span><span class="sxs-lookup"><span data-stu-id="908aa-141">By having a data contract implement the <xref:System.Runtime.Serialization.IExtensibleDataObject> interface, one can allow the <xref:System.Runtime.Serialization.DataContractSerializer> to pass members defined in newer versions of a data contract through applications with earlier versions of the contract.</span></span>  
  
 <span data-ttu-id="908aa-142">Independentemente de todas as diferenças, o XML em que o <xref:System.Xml.Serialization.XmlSerializer> serializa um tipo é, por padrão, semanticamente idêntico ao XML em que o <xref:System.Runtime.Serialization.DataContractSerializer> serializa um tipo, desde que o namespace do XML seja explicitamente definido.</span><span class="sxs-lookup"><span data-stu-id="908aa-142">Despite all of the differences, the XML into which the <xref:System.Xml.Serialization.XmlSerializer> serializes a type by default is semantically identical to the XML into which the <xref:System.Runtime.Serialization.DataContractSerializer> serializes a type, provided the namespace for the XML is explicitly defined.</span></span> <span data-ttu-id="908aa-143">A classe a seguir, que tem atributos para uso com ambos os serializadores, é convertida em um XML semanticamente idêntico pelo <xref:System.Xml.Serialization.XmlSerializer> e pelo <xref:System.Runtime.Serialization.DataContractAttribute>:</span><span class="sxs-lookup"><span data-stu-id="908aa-143">The following class, which has attributes for use with both of the serializers, are translated into semantically identical XML by the <xref:System.Xml.Serialization.XmlSerializer> and by the <xref:System.Runtime.Serialization.DataContractAttribute>:</span></span>  
  
```  
[Serializable]  
[XmlRoot(Namespace="urn:Contoso:2006:January:29")]  
[DataContract(Namespace="urn:Contoso:2006:January:29")]  
public class LineItem  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
```  
  
 <span data-ttu-id="908aa-144">O Windows software development kit (SDK) inclui uma ferramenta de linha de comando chamada a [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Como a ferramenta de xsd.exe usada com serviços Web do ASP.NET, Svcutil.exe pode gerar definições de tipos de dados .NET do esquema XML.</span><span class="sxs-lookup"><span data-stu-id="908aa-144">The Windows software development kit (SDK) includes a command-line tool called the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).Like the xsd.exe tool used with ASP.NET Web services, Svcutil.exe can generate definitions of .NET data types from XML Schema.</span></span> <span data-ttu-id="908aa-145">Os tipos serão contratos de dados se o <xref:System.Runtime.Serialization.DataContractSerializer> puder emitir o XML no formato definido pelo Esquema XML; caso contrário, eles serão destinados à serialização por meio do <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="908aa-145">The types are data contracts if the <xref:System.Runtime.Serialization.DataContractSerializer> can emit XML in the format defined by the XML Schema; otherwise, they are intended for serialization using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="908aa-146">A ferramenta Svcutil.exe também pode ser criada para gerar o Esquema XML a partir de contratos de dados usando a respectiva opção `/dataContractOnly`.</span><span class="sxs-lookup"><span data-stu-id="908aa-146">The tool, Svcutil.exe, can also be made to generate XML Schema from data contracts using its `/dataContractOnly` switch.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="908aa-147">Embora os serviços Web ASP.NET usem o <xref:System.Xml.Serialization.XmlSerializer>, e o modo de compatibilidade com ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faça com que os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] simulem o comportamento dos serviços Web ASP.NET, a opção de compatibilidade com o ASP.NET não restringe o uso do <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="908aa-147">Although ASP.NET Web services use the <xref:System.Xml.Serialization.XmlSerializer>, and [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode makes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services mimic the behavior of ASP.NET Web services, the ASP.NET compatibility option does not restrict one to using the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="908aa-148">É possível ainda usar o <xref:System.Runtime.Serialization.DataContractSerializer> com os serviços em execução no modo de compatibilidade com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-148">One can still use the <xref:System.Runtime.Serialization.DataContractSerializer> with services running in the ASP.NET compatibility mode.</span></span>  
  
## <a name="service-development"></a><span data-ttu-id="908aa-149">Desenvolvimento do serviço</span><span class="sxs-lookup"><span data-stu-id="908aa-149">Service Development</span></span>  
 <span data-ttu-id="908aa-150">Para desenvolver um serviço usando o ASP.NET, é comum adicionar o atributo <xref:System.Web.Services.WebService> a uma classe e o <xref:System.Web.Services.WebMethodAttribute> a qualquer método dessa classe que será uma operação do serviço:</span><span class="sxs-lookup"><span data-stu-id="908aa-150">To develop a service using ASP.NET, it has been customary to add the <xref:System.Web.Services.WebService> attribute to a class, and the <xref:System.Web.Services.WebMethodAttribute> to any of that class’ methods that are to be operations of the service:</span></span>  
  
```  
[WebService]  
public class Service : T:System.Web.Services.WebService  
{  
    [WebMethod]  
    public string Echo(string input)   
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="908aa-151">O ASP.NET 2.0 permite adicionar os atributos <xref:System.Web.Services.WebService> e <xref:System.Web.Services.WebMethodAttribute> a uma interface, e não a uma classe, e gravar uma classe para implementar a interface:</span><span class="sxs-lookup"><span data-stu-id="908aa-151">ASP.NET 2.0 introduced the option of adding the attribute <xref:System.Web.Services.WebService> and <xref:System.Web.Services.WebMethodAttribute> to an interface rather than to a class, and writing a class to implement the interface:</span></span>  
  
```  
[WebService]  
public interface IEcho  
{  
    [WebMethod]  
    string Echo(string input);  
}  
  
public class Service : IEcho  
{  
  
   public string Echo(string input)  
   {  
        return input;  
    }  
}  
```  
  
 <span data-ttu-id="908aa-152">O uso dessa opção deve ser preferencial, pois a interface com o atributo <xref:System.Web.Services.WebService> constitui um contrato das operações executadas pelo serviço que podem ser reutilizadas com várias classes, que, por sua vez, podem implementar o mesmo contrato de diferentes maneiras.</span><span class="sxs-lookup"><span data-stu-id="908aa-152">Using this option is to be preferred, because the interface with the <xref:System.Web.Services.WebService> attribute constitutes a contract for the operations performed by the service that can be reused with various classes that might implement that same contract in different ways.</span></span>  
  
 <span data-ttu-id="908aa-153">Um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é fornecido através da definição de um ou mais pontos de extremidade do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-153">A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is provided by defining one or more [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoints.</span></span> <span data-ttu-id="908aa-154">Um ponto de extremidade é definido por um endereço, uma associação e um contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-154">An endpoint is defined by an address, a binding and a service contract.</span></span> <span data-ttu-id="908aa-155">O endereço define em que local o serviço está localizado.</span><span class="sxs-lookup"><span data-stu-id="908aa-155">The address defines where the service is located.</span></span> <span data-ttu-id="908aa-156">A associação especifica como se comunicar com o serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-156">The binding specifies how to communicate with the service.</span></span> <span data-ttu-id="908aa-157">O contrato de serviço define as operações que o serviço pode executar.</span><span class="sxs-lookup"><span data-stu-id="908aa-157">The service contract defines the operations that the service can perform.</span></span>  
  
 <span data-ttu-id="908aa-158">O contrato de serviço geralmente é definido primeiro, adicionando o <xref:System.ServiceModel.ServiceContractAttribute> e o <xref:System.ServiceModel.OperationContractAttribute> a uma interface:</span><span class="sxs-lookup"><span data-stu-id="908aa-158">The service contract is usually defined first, by adding <xref:System.ServiceModel.ServiceContractAttribute> and <xref:System.ServiceModel.OperationContractAttribute> to an interface:</span></span>  
  
```  
[ServiceContract]  
public interface IEcho  
{  
     [OperationContract]  
     string Echo(string input);  
}  
```  
  
 <span data-ttu-id="908aa-159">O <xref:System.ServiceModel.ServiceContractAttribute> especifica que a interface define um contrato de serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], e o <xref:System.ServiceModel.OperationContractAttribute> indica quais métodos da interface, se houver algum, definem operações do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-159">The <xref:System.ServiceModel.ServiceContractAttribute> specifies that the interface defines a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service contract, and the <xref:System.ServiceModel.OperationContractAttribute> indicates which, if any, of the methods of the interface define operations of the service contract.</span></span>  
  
 <span data-ttu-id="908aa-160">Depois que um contrato de serviço for definido, ele será implementado em uma classe, permitindo que esta implemente a interface através da qual o contrato de serviço será definido:</span><span class="sxs-lookup"><span data-stu-id="908aa-160">Once a service contract has been defined, it is implemented in a class, by having the class implement the interface by which the service contract is defined:</span></span>  
  
```  
public class Service : IEcho  
{  
    public string Echo(string input)  
    {  
       return input;  
    }  
}  
```  
  
 <span data-ttu-id="908aa-161">Uma classe que implementa um contrato de serviço é denominada tipo de serviço no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-161">A class that implements a service contract is referred to as a service type in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 <span data-ttu-id="908aa-162">A próxima etapa é vincular um endereço e uma associação a um tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-162">The next step is to associate an address and a binding with a service type.</span></span> <span data-ttu-id="908aa-163">Isso geralmente é feito em um arquivo de configuração, editando o arquivo diretamente ou usando um editor de configuração fornecido com o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-163">That is typically done in a configuration file, either by editing the file directly, or by using a configuration editor provided with [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="908aa-164">Aqui está um exemplo de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="908aa-164">Here is an example of a configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
     <system.serviceModel>  
      <services>  
      <service name="Service ">  
       <endpoint   
        address="EchoService"  
        binding="basicHttpBinding"  
        contract="IEchoService "/>  
      </service>  
      </services>  
     </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="908aa-165">A associação especifica o conjunto de protocolos que será usado para estabelecer a comunicação com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="908aa-165">The binding specifies the set of protocols for communicating with the application.</span></span> <span data-ttu-id="908aa-166">A tabela a seguir lista as associações fornecidas pelo sistema que representam opções comuns.</span><span class="sxs-lookup"><span data-stu-id="908aa-166">The following table lists the system-provided bindings that represent common options.</span></span>  
  
|<span data-ttu-id="908aa-167">Nome</span><span class="sxs-lookup"><span data-stu-id="908aa-167">Name</span></span>|<span data-ttu-id="908aa-168">Finalidade</span><span class="sxs-lookup"><span data-stu-id="908aa-168">Purpose</span></span>|  
|----------|-------------|  
|<span data-ttu-id="908aa-169">BasicHttpBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-169">BasicHttpBinding</span></span>|<span data-ttu-id="908aa-170">Interoperabilidade com serviços e clientes Web que oferecem suporte ao WS-BasicProfile 1.1 e ao Basic Security Profile 1.0.</span><span class="sxs-lookup"><span data-stu-id="908aa-170">Interoperability with Web services and clients supporting the WS-BasicProfile 1.1 and Basic Security Profile 1.0.</span></span>|  
|<span data-ttu-id="908aa-171">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-171">WSHttpBinding</span></span>|<span data-ttu-id="908aa-172">Interoperabilidade com serviços e clientes Web que oferecem suporte aos protocolos WS-* sobre HTTP.</span><span class="sxs-lookup"><span data-stu-id="908aa-172">Interoperability with Web services and clients that support the WS-* protocols over HTTP.</span></span>|  
|<span data-ttu-id="908aa-173">WSDualHttpBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-173">WSDualHttpBinding</span></span>|<span data-ttu-id="908aa-174">Comunicação HTTP duplex através da qual o receptor de uma mensagem inicial não responde diretamente ao remetente inicial, mas pode transmitir qualquer número de respostas durante um período usando o protocolo HTTP em conformidade com os protocolos WS-*.</span><span class="sxs-lookup"><span data-stu-id="908aa-174">Duplex HTTP communication, by which the receiver of an initial message does not reply directly to the initial sender, but may transmit any number of responses over a period of time by using HTTP in conformity with WS-* protocols.</span></span>|  
|<span data-ttu-id="908aa-175">WSFederationBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-175">WSFederationBinding</span></span>|<span data-ttu-id="908aa-176">Comunicação HTTP, em que o acesso aos recursos de um serviço pode ser controlado com base nas credenciais emitidas por um provedor de credenciais explicitamente identificado.</span><span class="sxs-lookup"><span data-stu-id="908aa-176">HTTP communication, in which access to the resources of a service can be controlled based on credentials issued by an explicitly-identified credential provider.</span></span>|  
|<span data-ttu-id="908aa-177">NetTcpBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-177">NetTcpBinding</span></span>|<span data-ttu-id="908aa-178">Comunicação segura, confiável e de alto desempenho entre as entidades de software do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em uma rede.</span><span class="sxs-lookup"><span data-stu-id="908aa-178">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities across a network.</span></span>|  
|<span data-ttu-id="908aa-179">NetNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-179">NetNamedPipeBinding</span></span>|<span data-ttu-id="908aa-180">Comunicação segura, confiável e de alto desempenho entre as entidades de software do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] no mesmo computador.</span><span class="sxs-lookup"><span data-stu-id="908aa-180">Secure, reliable, high-performance communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities on the same machine.</span></span>|  
|<span data-ttu-id="908aa-181">NetMsmqBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-181">NetMsmqBinding</span></span>|<span data-ttu-id="908aa-182">Comunicação entre entidades de software do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usando o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="908aa-182">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using MSMQ.</span></span>|  
|<span data-ttu-id="908aa-183">MsmqIntegrationBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-183">MsmqIntegrationBinding</span></span>|<span data-ttu-id="908aa-184">Comunicação entre uma entidade de software do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] e outra entidade de software usando o MSMQ.</span><span class="sxs-lookup"><span data-stu-id="908aa-184">Communication between a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entity and another software entity by using MSMQ.</span></span>|  
|<span data-ttu-id="908aa-185">NetPeerTcpBinding</span><span class="sxs-lookup"><span data-stu-id="908aa-185">NetPeerTcpBinding</span></span>|<span data-ttu-id="908aa-186">Comunicação entre entidades de software do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usando a Rede Ponto a Ponto do Windows.</span><span class="sxs-lookup"><span data-stu-id="908aa-186">Communication between [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] software entities by using Windows Peer-to-Peer Networking.</span></span>|  
  
 <span data-ttu-id="908aa-187">A associação fornecida pelo sistema, <xref:System.ServiceModel.BasicHttpBinding>, incorpora o conjunto de protocolos com suporte nos serviços Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-187">The system-provided binding, <xref:System.ServiceModel.BasicHttpBinding>, incorporates the set of protocols supported by ASP.NET Web services.</span></span>  
  
 <span data-ttu-id="908aa-188">As associações personalizadas para aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são facilmente definidas como coleções de classes de elemento de associação usadas pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para implementar protocolos individuais.</span><span class="sxs-lookup"><span data-stu-id="908aa-188">Custom bindings for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are easily defined as collections of the binding element classes that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses to implement individual protocols.</span></span> <span data-ttu-id="908aa-189">Novos elementos de associação podem ser gravados para representar protocolos adicionais.</span><span class="sxs-lookup"><span data-stu-id="908aa-189">New binding elements can be written to represent additional protocols.</span></span>  
  
 <span data-ttu-id="908aa-190">O comportamento interno dos tipos de serviço pode ser ajustado através das propriedades de uma família de classes denominada comportamentos.</span><span class="sxs-lookup"><span data-stu-id="908aa-190">The internal behavior of service types can be adjusted using the properties of a family of classes called behaviors.</span></span> <span data-ttu-id="908aa-191">Aqui, a classe <xref:System.ServiceModel.ServiceBehaviorAttribute> é usada para especificar que o tipo de serviço será multi-threaded.</span><span class="sxs-lookup"><span data-stu-id="908aa-191">Here, the <xref:System.ServiceModel.ServiceBehaviorAttribute> class is used to specify that the service type is to be multithreaded.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple]  
public class DerivativesCalculatorServiceType: IDerivativesCalculator  
```  
  
 <span data-ttu-id="908aa-192">Alguns comportamentos, como o <xref:System.ServiceModel.ServiceBehaviorAttribute>, são atributos.</span><span class="sxs-lookup"><span data-stu-id="908aa-192">Some behaviors, like <xref:System.ServiceModel.ServiceBehaviorAttribute>, are attributes.</span></span> <span data-ttu-id="908aa-193">Outros, os que têm propriedades que os administradores talvez queiram definir, podem ser modificados na configuração de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="908aa-193">Others, the ones with properties that administrators would want to set, can be modified in the configuration of an application.</span></span>  
  
 <span data-ttu-id="908aa-194">Nos tipos de serviço de programação, a classe <xref:System.ServiceModel.OperationContext> é usada frequentemente.</span><span class="sxs-lookup"><span data-stu-id="908aa-194">In programming service types, frequent use is made of the <xref:System.ServiceModel.OperationContext> class.</span></span> <span data-ttu-id="908aa-195">Sua propriedade estática <xref:System.ServiceModel.OperationContext.Current%2A> fornece acesso a informações sobre o contexto em que uma operação está sendo executada.</span><span class="sxs-lookup"><span data-stu-id="908aa-195">Its static <xref:System.ServiceModel.OperationContext.Current%2A> property provides access to information about the context in which an operation is running.</span></span> <span data-ttu-id="908aa-196">O <xref:System.ServiceModel.OperationContext> é semelhante às classes <xref:System.Web.HttpContext> e <xref:System.EnterpriseServices.ContextUtil>.</span><span class="sxs-lookup"><span data-stu-id="908aa-196"><xref:System.ServiceModel.OperationContext> is similar to both the <xref:System.Web.HttpContext> and <xref:System.EnterpriseServices.ContextUtil> classes.</span></span>  
  
## <a name="hosting"></a><span data-ttu-id="908aa-197">Hospedagem</span><span class="sxs-lookup"><span data-stu-id="908aa-197">Hosting</span></span>  
 <span data-ttu-id="908aa-198">Os serviços Web ASP.NET são compilados em um assembly de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="908aa-198">ASP.NET Web services are compiled into a class library assembly.</span></span> <span data-ttu-id="908aa-199">Um arquivo denominado arquivo de serviço é fornecido, com a extensão .asmx, contendo uma diretiva `@ WebService` que identifica a classe que contém o código do serviço e o assembly em que ele está localizado.</span><span class="sxs-lookup"><span data-stu-id="908aa-199">A file called the service file is provided that has the extension .asmx and contains an `@ WebService` directive that identifies the class that contains the code for the service and the assembly in which it is located.</span></span>  
  
```  
<%@ WebService Language="C#" Class="Service,ServiceAssembly" %>  
```  
  
 <span data-ttu-id="908aa-200">O arquivo de serviço é copiado para um aplicativo ASP.NET nos Serviços de Informações da Internet (IIS), e o assembly é copiado para o subdiretório \bin dessa raiz de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="908aa-200">The service file is copied into an ASP.NET application root in Internet Information Services (IIS), and the assembly is copied into the \bin subdirectory of that application root.</span></span> <span data-ttu-id="908aa-201">O aplicativo pode, então, ser acessado através do URL do arquivo de serviço na raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="908aa-201">The application is then accessible by using the uniform resource locator (URL) of the service file in the application root.</span></span>  
  
 <span data-ttu-id="908aa-202">Os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podem ser hospedados rapidamente no IIS 5.1 ou 6.0, no Serviço de Ativação de Processos do Windows (WAS) que é fornecido como parte do IIS 7.0 e em qualquer aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-202">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services can readily be hosted within IIS 5.1 or 6.0, the Windows Process Activation Service (WAS) that is provided as part of IIS 7.0, and within any .NET application.</span></span> <span data-ttu-id="908aa-203">Para hospedar um serviço no IIS 5.1 ou 6.0, o serviço deve usar o HTTP como protocolo de transporte de comunicação.</span><span class="sxs-lookup"><span data-stu-id="908aa-203">To host a service in IIS 5.1 or 6.0, the service must use HTTP as the communications transport protocol.</span></span>  
  
 <span data-ttu-id="908aa-204">Para hospedar um serviço no IIS 5.1 ou 6.0, ou no WAS, siga estas etapas:</span><span class="sxs-lookup"><span data-stu-id="908aa-204">To host a service within IIS 5.1, 6.0 or within WAS, use the follows steps:</span></span>  
  
1.  <span data-ttu-id="908aa-205">Compile o tipo de serviço em um assembly de biblioteca de classes.</span><span class="sxs-lookup"><span data-stu-id="908aa-205">Compile the service type into a class library assembly.</span></span>  
  
2.  <span data-ttu-id="908aa-206">Crie um arquivo de serviço com uma extensão .svc com uma diretiva `@ ServiceHost` para identificar o tipo de serviço:</span><span class="sxs-lookup"><span data-stu-id="908aa-206">Create a service file with a .svc extension with an `@ ServiceHost` directive to identify the service type:</span></span>  
  
    ```  
    <%@ServiceHost language="c#" Service="MyService" %>  
    ```  
  
3.  <span data-ttu-id="908aa-207">Copie o arquivo de serviço para um diretório virtual e o assembly para o subdiretório \bin desse diretório virtual.</span><span class="sxs-lookup"><span data-stu-id="908aa-207">Copy the service file into a virtual directory, and the assembly into the \bin subdirectory of that virtual directory.</span></span>  
  
4.  <span data-ttu-id="908aa-208">Copie o arquivo de configuração para o diretório virtual e atribua o nome Web.config a ele.</span><span class="sxs-lookup"><span data-stu-id="908aa-208">Copy the configuration file into the virtual directory, and name it Web.config.</span></span>  
  
 <span data-ttu-id="908aa-209">O aplicativo poderá, então, ser acessado através do URL do arquivo de serviço na raiz do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="908aa-209">The application is then accessible by using the URL of the service file in the application root.</span></span>  
  
 <span data-ttu-id="908aa-210">Para hospedar um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em um aplicativo .NET, compile o tipo de serviço em um assembly de biblioteca de classes referenciado pelo aplicativo e programe o aplicativo para hospedar o serviço usando a classe <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="908aa-210">To host a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service within a .NET application, compile the service type into a class library assembly referenced by the application, and program the application to host the service using the <xref:System.ServiceModel.ServiceHost> class.</span></span> <span data-ttu-id="908aa-211">Este é um exemplo da programação básica necessária:</span><span class="sxs-lookup"><span data-stu-id="908aa-211">The following is an example of the basic programming required:</span></span>  
  
```  
string httpBaseAddress = "http://www.contoso.com:8000/";  
string tcpBaseAddress = "net.tcp://www.contoso.com:8080/";  
  
Uri httpBaseAddressUri = new Uri(httpBaseAddress);  
Uri tcpBaseAddressUri = new Uri(tcpBaseAddress);  
  
Uri[] baseAdresses = new Uri[] {   
 httpBaseAddressUri,  
 tcpBaseAddressUri};  
  
using(ServiceHost host = new ServiceHost(  
typeof(Service), //"Service" is the name of the service type baseAdresses))  
{  
     host.Open();  
  
     […] //Wait to receive messages  
     host.Close();  
}  
```  
  
 <span data-ttu-id="908aa-212">Este exemplo mostra como os endereços de um ou mais protocolos de transporte são especificados na construção de um <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="908aa-212">This example shows how addresses for one or more transport protocols are specified in the construction of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="908aa-213">Esses endereços são chamados de endereços básicos.</span><span class="sxs-lookup"><span data-stu-id="908aa-213">These addresses are referred to as base addresses.</span></span>  
  
 <span data-ttu-id="908aa-214">O endereço fornecido para qualquer ponto de extremidade de um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é um endereço relativo a um endereço básico do host do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="908aa-214">The address provided for any endpoint of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is an address relative to a base address of the endpoint’s host.</span></span> <span data-ttu-id="908aa-215">O host pode ter um endereço básico para cada protocolo de transporte de comunicação.</span><span class="sxs-lookup"><span data-stu-id="908aa-215">The host can have one base address for each communication transport protocol.</span></span> <span data-ttu-id="908aa-216">Na configuração de exemplo do arquivo de configuração anterior, o <xref:System.ServiceModel.BasicHttpBinding> selecionado para o ponto de extremidade usa o HTTP como protocolo de transporte; portanto, o endereço do ponto de extremidade, `EchoService`, é relativo ao endereço básico HTTP do host.</span><span class="sxs-lookup"><span data-stu-id="908aa-216">In the sample configuration in the preceding configuration file, the <xref:System.ServiceModel.BasicHttpBinding> selected for the endpoint uses HTTP as the transport protocol, so the address of the endpoint, `EchoService`, is relative to the host’s HTTP base address.</span></span> <span data-ttu-id="908aa-217">No caso de host do exemplo anterior, o endereço básico HTTP é http://www.contoso.com:8000/.</span><span class="sxs-lookup"><span data-stu-id="908aa-217">In the case of the host in the preceding example, the HTTP base address is http://www.contoso.com:8000/.</span></span> <span data-ttu-id="908aa-218">Para um serviço hospedado no IIS ou no WAS, o endereço básico é a URL do arquivo do serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-218">For a service hosted within IIS or WAS, the base address is the URL of the service’s service file.</span></span>  
  
 <span data-ttu-id="908aa-219">Somente os serviços hospedados no IIS ou no WAS, e que são configurados com o HTTP como protocolo de transporte exclusivamente, podem usar a opção de modo de compatibilidade com o ASP.NET do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-219">Only services hosted in IIS or WAS, and which are configured with HTTP as the transport protocol exclusively, can be made to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ASP.NET compatibility mode option.</span></span> <span data-ttu-id="908aa-220">A ativação dessa opção exige as seguintes etapas.</span><span class="sxs-lookup"><span data-stu-id="908aa-220">Turning that option on requires the following steps.</span></span>  
  
1.  <span data-ttu-id="908aa-221">O programador deve adicionar o atributo <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> ao tipo de serviço e especificar se o modo de compatibilidade com o ASP.NET é permitido ou necessário.</span><span class="sxs-lookup"><span data-stu-id="908aa-221">The programmer must add the <xref:System.ServiceModel.Activation.AspNetCompatibilityRequirementsAttribute> attribute to the service type and specify that ASP.NET compatibility mode is either allowed or required.</span></span>  
  
    ```  
    [System.ServiceModel.Activation.AspNetCompatibilityRequirements(  
          RequirementsMode=AspNetCompatbilityRequirementsMode.Require)]  
    public class DerivativesCalculatorServiceType: IDerivativesCalculator  
    ```  
  
2.  <span data-ttu-id="908aa-222">O administrador deve configurar o aplicativo para usar o modo de compatibilidade com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-222">The administrator must configure the application to use the ASP.NET compatibility mode.</span></span>  
  
    ```xml  
    <configuration>  
         <system.serviceModel>  
          <services>  
          […]  
          </services>  
          <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="908aa-223">Os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também podem ser configurados para usar .asmx como extensão dos arquivos de serviço, em vez de usar .svc.</span><span class="sxs-lookup"><span data-stu-id="908aa-223">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to use .asmx as the extension for their service files rather than .svc.</span></span>  
  
    ```xml  
    <system.web>  
         <compilation>  
          <compilation debug="true">  
          <buildProviders>  
           <remove extension=".asmx"/>  
           <add extension=".asmx"   
            type="System.ServiceModel.ServiceBuildProvider,   
            Systemm.ServiceModel,   
            Version=3.0.0.0,   
            Culture=neutral,   
            PublicKeyToken=b77a5c561934e089" />  
          </buildProviders>  
          </compilation>  
         </compilation>  
    </system.web>  
    ```  
  
     <span data-ttu-id="908aa-224">Essa opção pode descartar a necessidade de modificar os clientes que estão configurados para usar as URLs dos arquivos de serviço .asmx ao modificar um serviço para usar o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-224">That option can save you from having to modify clients that are configured to use the URLs of .asmx service files when modifying a service to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="client-development"></a><span data-ttu-id="908aa-225">Desenvolvimento do cliente</span><span class="sxs-lookup"><span data-stu-id="908aa-225">Client Development</span></span>  
 <span data-ttu-id="908aa-226">Os clientes para serviços Web ASP.NET são gerados usando a ferramenta de linha de comando, WSDL.exe, que fornece o URL do arquivo .asmx como entrada.</span><span class="sxs-lookup"><span data-stu-id="908aa-226">Clients for ASP.NET Web services are generated using the command-line tool, WSDL.exe, which provides the URL of the .asmx file as input.</span></span> <span data-ttu-id="908aa-227">A ferramenta correspondente fornecida pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span><span class="sxs-lookup"><span data-stu-id="908aa-227">The corresponding tool provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span> <span data-ttu-id="908aa-228">Ela gera um módulo de código com a definição do contrato de serviço e a definição de uma classe de cliente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-228">It generates a code module with the definition of the service contract and the definition of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class.</span></span> <span data-ttu-id="908aa-229">Ela gera também um arquivo de configuração com o endereço e a associação do serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-229">It also generates a configuration file with the address and binding of the service.</span></span>  
  
 <span data-ttu-id="908aa-230">Ao programar o cliente de um serviço remoto, geralmente é aconselhável fazer isso de acordo com o padrão assíncrono.</span><span class="sxs-lookup"><span data-stu-id="908aa-230">In programming a client of a remote service it is generally advisable to program according to an asynchronous pattern.</span></span> <span data-ttu-id="908aa-231">O código gerado pela ferramenta WSDL.exe sempre fornece um modelo síncrono e um modelo assíncrono, por padrão.</span><span class="sxs-lookup"><span data-stu-id="908aa-231">The code generated by the WSDL.exe tool always provides for both a synchronous and an asynchronous pattern by default.</span></span> <span data-ttu-id="908aa-232">O código gerado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pode fornecer um padrão.</span><span class="sxs-lookup"><span data-stu-id="908aa-232">The code generated by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) can provide for either pattern.</span></span> <span data-ttu-id="908aa-233">Por padrão, ele é projetado para o modelo síncrono.</span><span class="sxs-lookup"><span data-stu-id="908aa-233">It provides for the synchronous pattern by default.</span></span> <span data-ttu-id="908aa-234">Se a ferramenta for executada com a opção `/async`, o código gerado será projetado para o modelo assíncrono.</span><span class="sxs-lookup"><span data-stu-id="908aa-234">If the tool is executed with the `/async` switch, then the generated code provides for the asynchronous pattern.</span></span>  
  
 <span data-ttu-id="908aa-235">Não há nenhuma garantia de que os nomes contidos nas classes de cliente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geradas pela ferramenta WSDL.exe do ASP.NET, por padrão, correspondam aos nomes contidos nas classes de cliente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] geradas pela ferramenta Svcutil.exe.</span><span class="sxs-lookup"><span data-stu-id="908aa-235">There is no guarantee that names in the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by ASP.NET’s WSDL.exe tool, by default, match the names in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client classes generated by the Svcutil.exe tool.</span></span> <span data-ttu-id="908aa-236">Em particular, os nomes das propriedades das classes que precisam ser serializadas por meio do <xref:System.Xml.Serialization.XmlSerializer> recebem, por padrão, o sufixo Property no código gerado pela ferramenta Svcutil.exe, o que não acontece com a ferramenta WSDL.exe.</span><span class="sxs-lookup"><span data-stu-id="908aa-236">In particular, the names of the properties of classes that have to be serialized using the <xref:System.Xml.Serialization.XmlSerializer> are, by default, given the suffix Property in the code generated by the Svcutil.exe tool, which is not the case with the WSDL.exe tool.</span></span>  
  
## <a name="message-representation"></a><span data-ttu-id="908aa-237">Representação da mensagem</span><span class="sxs-lookup"><span data-stu-id="908aa-237">Message Representation</span></span>  
 <span data-ttu-id="908aa-238">Os cabeçalhos das mensagens SOAP enviadas e recebidas por serviços Web ASP.NET podem ser personalizados.</span><span class="sxs-lookup"><span data-stu-id="908aa-238">The headers of the SOAP messages sent and received by ASP.NET Web services can be customized.</span></span> <span data-ttu-id="908aa-239">Uma classe é derivada do <xref:System.Web.Services.Protocols.SoapHeader> para definir a estrutura do cabeçalho e, em seguida, o <xref:System.Web.Services.Protocols.SoapHeaderAttribute> é usado para indicar a presença do cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="908aa-239">A class is derived from <xref:System.Web.Services.Protocols.SoapHeader> to define the structure of the header, and then the <xref:System.Web.Services.Protocols.SoapHeaderAttribute> is used to indicate the presence of the header.</span></span>  
  
```  
public class SomeProtocol : SoapHeader  
{  
     public long CurrentValue;  
     public long Total;  
}  
  
[WebService]  
public interface IEcho  
{  
     SomeProtocol ProtocolHeader  
     {  
      get;  
     set;  
     }  
  
     [WebMethod]  
     [SoapHeader("ProtocolHeader")]  
     string PlaceOrders(PurchaseOrderType order);  
}  
  
public class Service: WebService, IEcho  
{  
     private SomeProtocol protocolHeader;  
  
     public SomeProtocol ProtocolHeader  
     {  
         get  
         {  
              return this.protocolHeader;  
         }  
  
         set  
         {  
              this.protocolHeader = value;  
         }  
     }  
  
     string PlaceOrders(PurchaseOrderType order)  
     {  
         long currentValue = this.protocolHeader.CurrentValue;  
     }  
}  
```  
  
 <span data-ttu-id="908aa-240">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece os atributos, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute> e <xref:System.ServiceModel.MessageBodyMemberAttribute>, para descrever a estrutura das mensagens SOAP enviadas e recebidas por um serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-240">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides the attributes, <xref:System.ServiceModel.MessageContractAttribute>, <xref:System.ServiceModel.MessageHeaderAttribute>, and <xref:System.ServiceModel.MessageBodyMemberAttribute> to describe the structure of the SOAP messages sent and received by a service.</span></span>  
  
```  
[DataContract]  
public class SomeProtocol  
{  
     [DataMember]  
     public long CurrentValue;  
     [DataMember]  
     public long Total;  
}  
  
[DataContract]  
public class Item  
{  
     [DataMember]  
     public string ItemNumber;  
     [DataMember]  
     public decimal Quantity;  
     [DataMember]  
     public decimal UnitPrice;  
}  
  
[MessageContract]  
public class ItemMesage  
{  
     [MessageHeader]  
     public SomeProtocol ProtocolHeader;  
     [MessageBody]  
     public Item Content;  
}  
  
[ServiceContract]  
public interface IItemService  
{  
     [OperationContract]  
     public void DeliverItem(ItemMessage itemMessage);  
}  
```  
  
 <span data-ttu-id="908aa-241">Essa sintaxe produz uma representação explícita da estrutura das mensagens, enquanto a estrutura das mensagens está implícita no código de um serviço Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-241">This syntax yields an explicit representation of the structure of the messages, whereas the structure of messages is implied by the code of an ASP.NET Web service.</span></span> <span data-ttu-id="908aa-242">Além disso, na sintaxe do ASP.NET, os cabeçalhos das mensagens são representados como propriedades do serviço, como a propriedade `ProtocolHeader` no exemplo anterior, enquanto na sintaxe do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], eles são representados mais precisamente como propriedades das mensagens.</span><span class="sxs-lookup"><span data-stu-id="908aa-242">Also, in the ASP.NET syntax, message headers are represented as properties of the service, such as the `ProtocolHeader` property in the previous example, whereas in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] syntax, they are more accurately represented as properties of messages.</span></span> <span data-ttu-id="908aa-243">Além disso, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] permite que os cabeçalhos das mensagens sejam adicionados à configuração dos pontos de extremidade.</span><span class="sxs-lookup"><span data-stu-id="908aa-243">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] allows message headers to be added to the configuration of endpoints.</span></span>  
  
```xml  
<service name="Service ">  
     <endpoint   
      address="EchoService"  
      binding="basicHttpBinding"  
      contract="IEchoService ">  
      <headers>  
      <dsig:X509Certificate   
       xmlns:dsig="http://www.w3.org/2000/09/xmldsig#">  
       ...  
      </dsig:X509Certificate>  
      </headers>  
     </endpoint>  
</service>  
```  
  
 <span data-ttu-id="908aa-244">Essa opção permite que você evite qualquer referência aos cabeçalhos de protocolo infraestruturais no código de um cliente ou serviço: os cabeçalhos são adicionados às mensagens devido à forma como o ponto de extremidade é configurado.</span><span class="sxs-lookup"><span data-stu-id="908aa-244">That option allows you to avoid any reference to infrastructural protocol headers in the code for a client or service: the headers are added to messages because of how the endpoint is configured.</span></span>  
  
## <a name="service-description"></a><span data-ttu-id="908aa-245">Descrição do serviço</span><span class="sxs-lookup"><span data-stu-id="908aa-245">Service Description</span></span>  
 <span data-ttu-id="908aa-246">A emissão de uma solicitação HTTP GET para o arquivo .asmx de um serviço Web ASP.NET com a consulta WSDL faz com que o ASP.NET gere o WSDL para descrever o serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-246">Issuing an HTTP GET request for the .asmx file of an ASP.NET Web service with the query WSDL causes ASP.NET to generate WSDL to describe the service.</span></span> <span data-ttu-id="908aa-247">Ela retorna esse WSDL como a resposta à solicitação.</span><span class="sxs-lookup"><span data-stu-id="908aa-247">It returns that WSDL as the response to the request.</span></span>  
  
 <span data-ttu-id="908aa-248">O ASP.NET 2.0 possibilitou a validação da compatibilidade de um serviço com o Basic Profile 1.1 da Web Services-Interoperability Organization (WS-I) e a inserção de uma declaração de que o serviço é compatível em seu WSDL.</span><span class="sxs-lookup"><span data-stu-id="908aa-248">ASP.NET 2.0 made it possible to validate that a service is compliant with the Basic Profile 1.1 of the Web Services-Interoperability Organization (WS-I), and to insert a claim that the service is compliant into its WSDL.</span></span> <span data-ttu-id="908aa-249">Isso é feito por meio dos parâmetros `ConformsTo` e `EmitConformanceClaims` do atributo <xref:System.Web.Services.WebServiceBindingAttribute>.</span><span class="sxs-lookup"><span data-stu-id="908aa-249">That is done using the `ConformsTo` and `EmitConformanceClaims` parameters of the <xref:System.Web.Services.WebServiceBindingAttribute> attribute.</span></span>  
  
```  
[WebService(Namespace = "http://tempuri.org/")]  
[WebServiceBinding(  
     ConformsTo = WsiProfiles.BasicProfile1_1,  
     EmitConformanceClaims=true)]  
public interface IEcho  
```  
  
 <span data-ttu-id="908aa-250">O WSDL que o ASP.NET gera para um serviço pode ser personalizado.</span><span class="sxs-lookup"><span data-stu-id="908aa-250">The WSDL that ASP.NET generates for a service can be customized.</span></span> <span data-ttu-id="908aa-251">As personalizações são feitas através da criação de uma classe do <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> para adicionar itens ao WSDL.</span><span class="sxs-lookup"><span data-stu-id="908aa-251">Customizations are made by creating a derived class of <xref:System.Web.Services.Description.ServiceDescriptionFormatExtension> to add items to the WSDL.</span></span>  
  
 <span data-ttu-id="908aa-252">A emissão de uma solicitação HTTP GET com a consulta WSDL do arquivo .svc de um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] com um ponto de extremidade HTTP hospedado no IIS 5.1, 6.0 ou WAS faz com que o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] responda ao WSDL para descrever o serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-252">Issuing an HTTP GET request with the query WSDL for the .svc file of a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with an HTTP endpoint hosted within IIS 51, 6.0 or WAS causes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] to respond with WSDL to describe the service.</span></span> <span data-ttu-id="908aa-253">A emissão de uma solicitação HTTP GET com a consulta WSDL para o endereço básico HTTP de um serviço hospedado em um aplicativo .NET terá o mesmo efeito se httpGetEnabled for definido como true.</span><span class="sxs-lookup"><span data-stu-id="908aa-253">Issuing an HTTP GET request with the query WSDL to the HTTP base address of a service hosted within a .NET application has the same effect if httpGetEnabled is set to true.</span></span>  
  
 <span data-ttu-id="908aa-254">No entanto, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também responde às solicitações WS-MetadataExchange com o WSDL gerado por ele para descrever um serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-254">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] also responds to WS-MetadataExchange requests with WSDL that it generates to describe a service.</span></span> <span data-ttu-id="908aa-255">Os Serviços Web ASP.NET não têm suporte interno para solicitações WS-MetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="908aa-255">ASP.NET Web services do not have built-in support for WS-MetadataExchange requests.</span></span>  
  
 <span data-ttu-id="908aa-256">O WSDL gerado pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pode ser amplamente personalizado.</span><span class="sxs-lookup"><span data-stu-id="908aa-256">The WSDL that [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generates can be extensively customized.</span></span> <span data-ttu-id="908aa-257">A classe <xref:System.ServiceModel.Description.ServiceMetadataBehavior> fornece alguns recursos para a personalização do WSDL.</span><span class="sxs-lookup"><span data-stu-id="908aa-257">The <xref:System.ServiceModel.Description.ServiceMetadataBehavior> class provides some facilities for customizing the WSDL.</span></span> <span data-ttu-id="908aa-258">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também pode ser configurado para não gerar o WSDL, mas para usar um arquivo WSDL estático em uma determinada URL.</span><span class="sxs-lookup"><span data-stu-id="908aa-258">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] can also be configured to not generate WSDL, but rather to use a static WSDL file at a given URL.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DescriptionBehavior">  
     <metadataPublishing   
      enableMetadataExchange="true"   
      enableGetWsdl="true"   
      enableHelpPage="true"   
      metadataLocation=  
      "http://localhost/DerivativesCalculatorService/Service.WSDL"/>  
     </behavior>  
</behaviors>  
```  
  
## <a name="exception-handling"></a><span data-ttu-id="908aa-259">Tratamento de Exceção</span><span class="sxs-lookup"><span data-stu-id="908aa-259">Exception Handling</span></span>  
 <span data-ttu-id="908aa-260">Nos serviços Web ASP.NET, as exceções não tratadas são retornadas aos clientes como falhas SOAP.</span><span class="sxs-lookup"><span data-stu-id="908aa-260">In ASP.NET Web services, unhandled exceptions are returned to clients as SOAP faults.</span></span> <span data-ttu-id="908aa-261">Você também pode lançar explicitamente as instâncias da classe <xref:System.Web.Services.Protocols.SoapException> e ter mais controle sobre o conteúdo da falha SOAP que é passada para o cliente.</span><span class="sxs-lookup"><span data-stu-id="908aa-261">You can also explicitly throw instances of the <xref:System.Web.Services.Protocols.SoapException> class and have more control over the content of the SOAP fault that gets transmitted to the client.</span></span>  
  
 <span data-ttu-id="908aa-262">Nos serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], as exceções não tratadas não são retornadas aos clientes como falhas SOAP, para evitar que informações confidenciais sejam divulgadas inadvertidamente através das exceções.</span><span class="sxs-lookup"><span data-stu-id="908aa-262">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services, unhandled exceptions are not returned to clients as SOAP faults to prevent sensitive information being inadvertently exposed through the exceptions.</span></span> <span data-ttu-id="908aa-263">Há uma configuração que permite que as exceções não tratadas sejam retornadas aos clientes para fins de depuração.</span><span class="sxs-lookup"><span data-stu-id="908aa-263">A configuration setting is provided to have unhandled exceptions returned to clients for the purpose of debugging.</span></span>  
  
 <span data-ttu-id="908aa-264">Para retornar falhas SOAP aos clientes, você pode lançar instâncias do tipo genérico, <xref:System.ServiceModel.FaultException%601>, usando o tipo de contrato de dados como tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="908aa-264">To return SOAP faults to clients, you can throw instances of the generic type, <xref:System.ServiceModel.FaultException%601>, using the data contract type as the generic type.</span></span> <span data-ttu-id="908aa-265">Você também pode adicionar atributos <xref:System.ServiceModel.FaultContractAttribute> às operações para especificar as falhas que uma operação pode produzir.</span><span class="sxs-lookup"><span data-stu-id="908aa-265">You can also add <xref:System.ServiceModel.FaultContractAttribute> attributes to operations to specify the faults that an operation might yield.</span></span>  
  
```  
[DataContract]  
public class MathFault  
{   
     [DataMember]  
     public string operation;  
     [DataMember]  
     public string problemType;  
}  
  
[ServiceContract]  
public interface ICalculator  
{  
     [OperationContract]  
     [FaultContract(typeof(MathFault))]  
     int Divide(int n1, int n2);  
}  
```  
  
 <span data-ttu-id="908aa-266">Isso fará com que as falhas possíveis sejam anunciadas no WSDL do serviço, permitindo que os programadores de cliente antevejam quais falhas podem resultar de uma operação e gravem as instruções catch apropriadas.</span><span class="sxs-lookup"><span data-stu-id="908aa-266">Doing so results in the possible faults being advertised in the WSDL for the service, allowing client programmers to anticipate which faults can result from an operation, and write the appropriate catch statements.</span></span>  
  
```  
try  
{  
     result = client.Divide(value1, value2);  
}  
catch (FaultException<MathFault> e)  
{  
 Console.WriteLine("FaultException<MathFault>: Math fault while doing "  
  + e.Detail.operation   
  + ". Problem: "   
  + e.Detail.problemType);  
}  
```  
  
## <a name="state-management"></a><span data-ttu-id="908aa-267">Gerenciamento do estado</span><span class="sxs-lookup"><span data-stu-id="908aa-267">State Management</span></span>  
 <span data-ttu-id="908aa-268">A classe usada para implementar um serviço Web ASP.NET pode ser derivada do <xref:System.Web.Services.WebService>.</span><span class="sxs-lookup"><span data-stu-id="908aa-268">The class used to implement an ASP.NET Web service may be derived from <xref:System.Web.Services.WebService>.</span></span>  
  
```  
public class Service : WebService, IEcho  
{  
  
 public string Echo(string input)  
 {  
  return input;  
 }  
}  
```  
  
 <span data-ttu-id="908aa-269">Nesse caso, a classe pode ser programada para usar a propriedade Context da classe base <xref:System.Web.Services.WebService> para acessar um objeto <xref:System.Web.HttpContext>.</span><span class="sxs-lookup"><span data-stu-id="908aa-269">In that case, the class can be programmed to use the <xref:System.Web.Services.WebService> base class’ Context property to access a <xref:System.Web.HttpContext> object.</span></span> <span data-ttu-id="908aa-270">O objeto <xref:System.Web.HttpContext> pode ser usado para atualizar e recuperar informações de estado do aplicativo por meio da propriedade Application, e pode ser usado para atualizar e recuperar informações de estado de sessão por meio da propriedade Session.</span><span class="sxs-lookup"><span data-stu-id="908aa-270">The <xref:System.Web.HttpContext> object can be used to update and retrieve application state information by using its Application property, and can be used to update and retrieve session state information by using its Session property.</span></span>  
  
 <span data-ttu-id="908aa-271">O ASP.NET fornece um controle considerável sobre o local onde as informações de estado de sessão acessadas por meio da propriedade Session do <xref:System.Web.HttpContext> são armazenadas.</span><span class="sxs-lookup"><span data-stu-id="908aa-271">ASP.NET provides considerable control over where the session state information accessed by using the Session property of the <xref:System.Web.HttpContext> is actually stored.</span></span> <span data-ttu-id="908aa-272">Elas podem ser armazenadas em cookies, em um banco de dados, na memória do servidor atual ou na memória de um servidor designado.</span><span class="sxs-lookup"><span data-stu-id="908aa-272">It may be stored in cookies, in a database, in the memory of the current server, or in the memory of a designated server.</span></span> <span data-ttu-id="908aa-273">A opção é feita no arquivo de configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-273">The choice is made in the service’s configuration file.</span></span>  
  
 <span data-ttu-id="908aa-274">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece objetos extensíveis para o gerenciamento de estado.</span><span class="sxs-lookup"><span data-stu-id="908aa-274">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] provides extensible objects for state management.</span></span> <span data-ttu-id="908aa-275">Os objetos extensíveis são objetos que implementam o <xref:System.ServiceModel.IExtensibleObject%601>.</span><span class="sxs-lookup"><span data-stu-id="908aa-275">Extensible objects are objects that implement <xref:System.ServiceModel.IExtensibleObject%601>.</span></span> <span data-ttu-id="908aa-276">Os objetos extensíveis mais importantes são <xref:System.ServiceModel.ServiceHostBase> e <xref:System.ServiceModel.InstanceContext>.</span><span class="sxs-lookup"><span data-stu-id="908aa-276">The most important extensible objects are <xref:System.ServiceModel.ServiceHostBase> and <xref:System.ServiceModel.InstanceContext>.</span></span> <span data-ttu-id="908aa-277">O `ServiceHostBase` permite que você mantenha o estado que todas as instâncias de todos os tipos de serviço no mesmo host podem acessar, enquanto o `InstanceContext` permite que você mantenha o estado que pode ser acessado por qualquer código em execução na mesma instância de um tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-277">`ServiceHostBase` allows you to maintain state that all of the instances of all of the service types on the same host can access, while `InstanceContext` allows you to maintain state that can be accessed by any code running within the same instance of a service type.</span></span>  
  
 <span data-ttu-id="908aa-278">Aqui, o tipo de serviço, `TradingSystem`, tem um <xref:System.ServiceModel.ServiceBehaviorAttribute> que especifica que todas as chamadas da mesma instância de cliente do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sejam roteadas para a mesma instância do tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-278">Here, the service type, `TradingSystem`, has a <xref:System.ServiceModel.ServiceBehaviorAttribute> that specifies that all calls from the same [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client instance are routed to the same instance of the service type.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode = InstanceContextMode.PerSession)]  
public class TradingSystem: ITradingService  
```  
  
 <span data-ttu-id="908aa-279">A classe, `DealData`, define o estado que pode ser acessado por qualquer código em execução na mesma instância de um tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-279">The class, `DealData`, defines state that can be accessed by any code running in the same instance of a service type.</span></span>  
  
```  
internal class DealData: IExtension<InstanceContext>  
{  
 public string DealIdentifier = null;  
 public Trade[] Trades = null;  
}  
```  
  
 <span data-ttu-id="908aa-280">No código do tipo de serviço que implementa uma das operações do contrato de serviço, um objeto de estado `DealData` é adicionado ao estado da instância atual do tipo de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-280">In the code of the service type that implements one of the operations of the service contract, a `DealData` state object is added to the state of the current instance of the service type.</span></span>  
  
```  
string ITradingService.BeginDeal()  
{  
 string dealIdentifier = Guid.NewGuid().ToString();  
 DealData state = new DealData(dealIdentifier);  
 OperationContext.Current.InstanceContext.Extensions.Add(state);  
 return dealIdentifier;  
}  
```  
  
 <span data-ttu-id="908aa-281">O objeto de estado pode, então, ser recuperado e modificado pelo código que implementa outras operações do contrato de serviço.</span><span class="sxs-lookup"><span data-stu-id="908aa-281">That state object can then be retrieved and modified by the code that implements another of the service contract’s operations.</span></span>  
  
```  
void ITradingService.AddTrade(Trade trade)  
{  
 DealData dealData =  OperationContext.Current.InstanceContext.Extensions.Find<DealData>();  
 dealData.AddTrade(trade);  
}  
```  
  
 <span data-ttu-id="908aa-282">Enquanto o ASP.NET fornece controle sobre o local onde as informações de estado da classe <xref:System.Web.HttpContext> são armazenadas, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], pelo menos na sua versão inicial, não fornece nenhum controle sobre o local onde os objetos extensíveis são armazenados.</span><span class="sxs-lookup"><span data-stu-id="908aa-282">Whereas ASP.NET provides control over where state information in the <xref:System.Web.HttpContext> class is actually stored, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], at least in its initial version, provides no control over where extensible objects are stored.</span></span> <span data-ttu-id="908aa-283">Essa é a razão pela qual o modo de compatibilidade com o ASP.NET é selecionado para um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-283">That constitutes the very best reason for selecting the ASP.NET compatibility mode for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="908aa-284">Se o gerenciamento de estado configurável for obrigatório, a opção pelo modo de compatibilidade com o ASP.NET permite que você use os recursos da classe <xref:System.Web.HttpContext> exatamente como eles são usados no ASP.NET e configure onde as informações de estado gerenciadas por meio da classe <xref:System.Web.HttpContext> são armazenadas.</span><span class="sxs-lookup"><span data-stu-id="908aa-284">If configurable state management is imperative, then opting for the ASP.NET compatibility mode allows you to use the facilities of the <xref:System.Web.HttpContext> class exactly as they are used in ASP.NET, and also to configure where state information managed by using the <xref:System.Web.HttpContext> class is stored.</span></span>  
  
## <a name="security"></a><span data-ttu-id="908aa-285">Segurança</span><span class="sxs-lookup"><span data-stu-id="908aa-285">Security</span></span>  
 <span data-ttu-id="908aa-286">As opções para proteger os serviços Web ASP.NET são as mesmas usadas para proteger qualquer aplicativo do IIS.</span><span class="sxs-lookup"><span data-stu-id="908aa-286">The options for securing ASP.NET Web services are those for securing any IIS application.</span></span> <span data-ttu-id="908aa-287">Como os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podem ser hospedados não apenas no IIS, mas também em qualquer executável do .NET, as opções para proteger os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] devem ser feitas independentemente dos recursos do IIS.</span><span class="sxs-lookup"><span data-stu-id="908aa-287">Because [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can be hosted not only within IIS but also within any .NET executable, the options for securing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications must be made independent from the facilities of IIS.</span></span> <span data-ttu-id="908aa-288">No entanto, os recursos fornecidos para serviços Web ASP.NET também estão disponíveis para os serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em execução no modo de compatibilidade com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-288">However, the facilities provided for ASP.NET Web services are also available for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-authentication"></a><span data-ttu-id="908aa-289">Segurança: autenticação</span><span class="sxs-lookup"><span data-stu-id="908aa-289">Security: Authentication</span></span>  
 <span data-ttu-id="908aa-290">O IIS fornece recursos para controlar o acesso aos aplicativos através dos quais você pode selecionar o acesso anônimo ou vários modos de autenticação: Autenticação do Windows, Autenticação Digest, Autenticação Básica e Autenticação do .NET Passport.</span><span class="sxs-lookup"><span data-stu-id="908aa-290">IIS provides facilities for controlling access to applications by which you can select either anonymous access or a variety of modes of authentication: Windows Authentication, Digest Authentication, Basic Authentication, and .NET Passport Authentication.</span></span> <span data-ttu-id="908aa-291">A opção Autenticação do Windows pode ser usada para controlar o acesso aos serviços Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-291">The Windows Authentication option can be used to control access to ASP.NET Web services.</span></span> <span data-ttu-id="908aa-292">No entanto, quando os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são hospedados no IIS, este deve ser configurado para permitir o acesso anônimo ao aplicativo, para que a autenticação possa ser gerenciada pelo próprio [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], que oferece suporte à autenticação do Windows entre várias outras opções.</span><span class="sxs-lookup"><span data-stu-id="908aa-292">However, when [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications are hosted within IIS, IIS must be configured to permit anonymous access to the application, so that authentication can be managed by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] itself, which does support Windows authentication among various other options.</span></span> <span data-ttu-id="908aa-293">As outras opções, que são internas, incluem tokens de nome de usuário, certificados X.509, tokens SAML e cartão CardSpace, mas os mecanismos de autenticação personalizados também podem ser definidos.</span><span class="sxs-lookup"><span data-stu-id="908aa-293">The other options that are built-in include username tokens, X.509 certificates, SAML tokens, and CardSpace card, but custom authentication mechanisms can also be defined.</span></span>  
  
### <a name="security-impersonation"></a><span data-ttu-id="908aa-294">Segurança: representação</span><span class="sxs-lookup"><span data-stu-id="908aa-294">Security: Impersonation</span></span>  
 <span data-ttu-id="908aa-295">O ASP.NET fornece um elemento de identidade através do qual um serviço Web ASP.NET pode ser feito para representar um usuário específico ou qualquer credencial do usuário fornecida com a solicitação atual.</span><span class="sxs-lookup"><span data-stu-id="908aa-295">ASP.NET provides an identity element by which an ASP.NET Web service can be made to impersonate a particular user or whichever user’s credentials are provided with the current request.</span></span> <span data-ttu-id="908aa-296">Esse elemento pode ser usado para configurar a representação em aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] em execução no modo de compatibilidade com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-296">That element can be used to configure impersonation in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications running in ASP.NET compatibility mode.</span></span>  
  
 <span data-ttu-id="908aa-297">O sistema de configuração do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fornece seu próprio elemento de identidade para designar um usuário específico para representar.</span><span class="sxs-lookup"><span data-stu-id="908aa-297">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] configuration system provides its own identity element for designating a particular user to impersonate.</span></span> <span data-ttu-id="908aa-298">Além disso, os clientes e serviços do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podem ser configurados independentemente para representação.</span><span class="sxs-lookup"><span data-stu-id="908aa-298">Also, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients and services can be independently configured for impersonation.</span></span> <span data-ttu-id="908aa-299">Os clientes podem ser configurados para representar o usuário atual quando eles transmitirem solicitações.</span><span class="sxs-lookup"><span data-stu-id="908aa-299">Clients can be configured to impersonate the current user when they transmit requests.</span></span>  
  
```xml  
<behaviors>  
     <behavior name="DerivativesCalculatorClientBehavior">  
      <clientCredentials>  
      <windows allowedImpersonationLevel="Impersonation"/>  
      </clientCredentials>  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="908aa-300">As operações de serviço podem ser configuradas para representar quaisquer credenciais do usuário fornecidas com a solicitação atual.</span><span class="sxs-lookup"><span data-stu-id="908aa-300">Service operations can be configured to impersonate whichever user’s credentials are provided with the current request.</span></span>  
  
```  
[OperationBehavior(Impersonation = ImpersonationOption.Required)]  
public void Receive(Message input)  
```  
  
### <a name="security-authorization-using-access-control-lists"></a><span data-ttu-id="908aa-301">Segurança: autorização por meio das listas de controle de acesso</span><span class="sxs-lookup"><span data-stu-id="908aa-301">Security: Authorization using Access Control Lists</span></span>  
 <span data-ttu-id="908aa-302">As listas de controle de acesso (ACLs) podem ser usadas para restringir o acesso a arquivos .asmx.</span><span class="sxs-lookup"><span data-stu-id="908aa-302">Access Control Lists (ACLs) can be used to restrict access to .asmx files.</span></span> <span data-ttu-id="908aa-303">No entanto, as ACLs em arquivos .svc do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] são ignoradas, exceto no modo de compatibilidade com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-303">However, ACLs on [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] .svc files are ignored except in ASP.NET compatibility mode.</span></span>  
  
### <a name="security-role-based-authorization"></a><span data-ttu-id="908aa-304">Segurança: autorização baseada em função</span><span class="sxs-lookup"><span data-stu-id="908aa-304">Security: Role-based Authorization</span></span>  
 <span data-ttu-id="908aa-305">A opção Autenticação do Windows do IIS pode ser usada em conjunto com o elemento de autorização fornecido pela linguagem de configuração do ASP.NET, para facilitar a autorização baseada em função dos serviços Web ASP.NET com base nos grupos do Windows aos quais os usuários são atribuídos.</span><span class="sxs-lookup"><span data-stu-id="908aa-305">The IIS Windows Authentication option can be used in conjunction with the authorization element provided by the ASP.NET configuration language to facilitate role-based authorization for ASP.NET Web services based on the Windows groups to which users are assigned.</span></span> <span data-ttu-id="908aa-306">O ASP.NET 2.0 introduziu um mecanismo de autorização baseada em função mais genérico: os provedores de função.</span><span class="sxs-lookup"><span data-stu-id="908aa-306">ASP.NET 2.0 introduced a more general role-based authorization mechanism: role providers.</span></span>  
  
 <span data-ttu-id="908aa-307">Os provedores de função são classes que implementam uma interface básica para obter informações sobre as funções às quais um usuário é atribuído, mas cada provedor de função sabe como recuperar essas informações de uma fonte diferente.</span><span class="sxs-lookup"><span data-stu-id="908aa-307">Role providers are classes that all implement a basic interface for enquiring about the roles to which a user is assigned, but each role provider knows how to retrieve that information from a different source.</span></span> <span data-ttu-id="908aa-308">O ASP.NET 2.0 fornece um provedor de função que pode recuperar as atribuições de função de um banco de dados do Microsoft SQL Server e outro que pode recuperar as atribuições de função do Gerenciador de Autorização do Windows Server 2003.</span><span class="sxs-lookup"><span data-stu-id="908aa-308">ASP.NET 2.0 provides a role provider that can retrieve role assignments from a Microsoft SQL Server database, and another that can retrieve role assignments from the Windows Server 2003 Authorization Manager.</span></span>  
  
 <span data-ttu-id="908aa-309">O mecanismo de provedor de função pode ser usado independentemente do ASP.NET em qualquer aplicativo .NET, incluindo um aplicativo do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="908aa-309">The role provider mechanism can actually be used independently of ASP.NET in any .NET application, including a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application.</span></span> <span data-ttu-id="908aa-310">A configuração de exemplo a seguir de um aplicativo do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] mostra como o uso de um provedor de função do ASP.NET é uma opção selecionada por meio do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="908aa-310">The following sample configuration for a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] application shows how the use of an ASP.NET role provider is an option selected by means of the <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<system.serviceModel>  
     <services>  
         <service name="Service.ResourceAccessServiceType"   
             behaviorConfiguration="ServiceBehavior">  
             <endpoint   
              address="ResourceAccessService"   
              binding="wsHttpBinding"   
              contract="Service.IResourceAccessContract"/>  
         </service>  
     </services>  
     <behaviors>  
       <behavior name="ServiceBehavior">  
       <serviceAuthorization principalPermissionMode="UseAspNetRoles"/>  
      </behavior>  
     </behaviors>  
</system.serviceModel>  
```  
  
### <a name="security-claims-based-authorization"></a><span data-ttu-id="908aa-311">Segurança: autorização baseada em declaração</span><span class="sxs-lookup"><span data-stu-id="908aa-311">Security: Claims-based Authorization</span></span>  
 <span data-ttu-id="908aa-312">Uma das inovações mais importantes do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] é seu suporte completo ao acesso de autorização a recursos protegidos com base em declarações.</span><span class="sxs-lookup"><span data-stu-id="908aa-312">One of the most important innovations of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is its thorough support for authorizing access to protected resources based on claims.</span></span> <span data-ttu-id="908aa-313">As declarações consistem em um tipo, um direito e um valor, uma carteira de habilitação, por exemplo.</span><span class="sxs-lookup"><span data-stu-id="908aa-313">Claims consist of a type, a right and a value, a drivers’ license, for example.</span></span> <span data-ttu-id="908aa-314">Ela cria um conjunto de declarações sobre o portador, uma delas é a data de nascimento do portador.</span><span class="sxs-lookup"><span data-stu-id="908aa-314">It makes a set of claims about the bearer, one of which is the bearer’s date of birth.</span></span> <span data-ttu-id="908aa-315">O tipo dessa declaração é a data de nascimento, enquanto o valor da declaração é a data de nascimento do motorista.</span><span class="sxs-lookup"><span data-stu-id="908aa-315">The type of that claim is date of birth, while the value of the claim is the driver’s birth date.</span></span> <span data-ttu-id="908aa-316">O direito que uma declaração confere ao portador especifica o que o portador pode fazer com o valor a declaração.</span><span class="sxs-lookup"><span data-stu-id="908aa-316">The right that a claim confers on the bearer specifies what the bearer can do with the claim’s value.</span></span> <span data-ttu-id="908aa-317">No caso da declaração da data de nascimento do motorista, o direito é a posse: o motorista possui a data de nascimento mas não pode, por exemplo, alterá-la.</span><span class="sxs-lookup"><span data-stu-id="908aa-317">In the case of the claim of the driver’s date of birth, the right is possession: the driver possesses that date of birth but cannot, for example, alter it.</span></span> <span data-ttu-id="908aa-318">Autorização baseada em declaração inclui a autorização baseada em função, pois as funções são um tipo de declaração.</span><span class="sxs-lookup"><span data-stu-id="908aa-318">Claims-based authorization encloses role-based authorization, because roles are a type of claim.</span></span>  
  
 <span data-ttu-id="908aa-319">A autorização baseada em declarações é realizada através da comparação de um conjunto de declarações com os requisitos de acesso da operação e, dependendo do resultado dessa comparação, conceder ou negar o acesso à operação.</span><span class="sxs-lookup"><span data-stu-id="908aa-319">Authorization based on claims is accomplished by comparing a set of claims to the access requirements of the operation and, depending on the outcome of that comparison, granting or denying access to the operation.</span></span> <span data-ttu-id="908aa-320">No [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], você pode especificar uma classe a ser usada para executar a autorização baseada em declaração, mais uma vez atribuindo um valor à propriedade `ServiceAuthorizationManager` do <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span><span class="sxs-lookup"><span data-stu-id="908aa-320">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], you can specify a class to use to run claims-based authorization, once again by assigning a value to the `ServiceAuthorizationManager` property of <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>.</span></span>  
  
```xml  
<behaviors>  
     <behavior name='ServiceBehavior'>  
     <serviceAuthorization   
     serviceAuthorizationManagerType=  
                   'Service.AccessChecker, Service' />  
     </behavior>  
</behaviors>  
```  
  
 <span data-ttu-id="908aa-321">As classes usadas para executar a autorização baseada em declarações devem derivar do <xref:System.ServiceModel.ServiceAuthorizationManager>, que tem apenas um método substituição, `AccessCheck()`.</span><span class="sxs-lookup"><span data-stu-id="908aa-321">Classes used to run claims-based authorization must derive from <xref:System.ServiceModel.ServiceAuthorizationManager>, which has just one method to override, `AccessCheck()`.</span></span> <span data-ttu-id="908aa-322">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] chama esse método sempre que uma operação do serviço é chamada e fornece um objeto <xref:System.ServiceModel.OperationContext>, que tem as declarações do usuário na propriedade `ServiceSecurityContext.AuthorizationContext`.</span><span class="sxs-lookup"><span data-stu-id="908aa-322">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] calls that method whenever an operation of the service is invoked and provides a <xref:System.ServiceModel.OperationContext> object, which has the claims for the user in its `ServiceSecurityContext.AuthorizationContext` property.</span></span> <span data-ttu-id="908aa-323">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] faz a montagem das declarações sobre o usuário de qualquer token de segurança fornecido pelo usuário para autenticação, que abandona a tarefa que avalia se essas declarações serão suficientes para a operação em questão.</span><span class="sxs-lookup"><span data-stu-id="908aa-323">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does the work of assembling claims about the user from whatever security token the user provided for authentication, which leaves the of task of evaluating whether those claims suffice for the operation in question.</span></span>  
  
 <span data-ttu-id="908aa-324">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que monta automaticamente as declarações de qualquer tipo de token de segurança é uma inovação altamente significativa, porque torna o código da autorização baseada nas declarações totalmente independentes do mecanismo de autenticação.</span><span class="sxs-lookup"><span data-stu-id="908aa-324">That [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] automatically assembles claims from any kind of security token is a highly significant innovation, because it makes the code for authorization based on the claims entirely independent of the authentication mechanism.</span></span> <span data-ttu-id="908aa-325">Por outro lado, a autorização que usa ACLs ou funções no ASP.NET está estreitamente associada à autenticação do Windows.</span><span class="sxs-lookup"><span data-stu-id="908aa-325">By contrast, authorization using ACLs or roles in ASP.NET is closely tied to Windows authentication.</span></span>  
  
### <a name="security-confidentiality"></a><span data-ttu-id="908aa-326">Segurança: confidencialidade</span><span class="sxs-lookup"><span data-stu-id="908aa-326">Security: Confidentiality</span></span>  
 <span data-ttu-id="908aa-327">A confidencialidade das mensagens trocadas com os serviços Web ASP.NET pode ser garantida no nível do transporte através da configuração do aplicativo no IIS para usar o protocolo HTTPS.</span><span class="sxs-lookup"><span data-stu-id="908aa-327">The confidentiality of messages exchanged with ASP.NET Web services can be ensured at the transport level by configuring the application within IIS to use the Secure Hypertext Transfer Protocol (HTTPS).</span></span> <span data-ttu-id="908aa-328">O mesmo pode ser feito para os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados no IIS.</span><span class="sxs-lookup"><span data-stu-id="908aa-328">The same can be done for [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted within IIS.</span></span> <span data-ttu-id="908aa-329">No entanto, os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hospedados fora do IIS também podem ser configurados para usar um protocolo de transporte seguro.</span><span class="sxs-lookup"><span data-stu-id="908aa-329">However, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications hosted outside of IIS can also be configured to use a secure transport protocol.</span></span> <span data-ttu-id="908aa-330">E o mais importante é que os aplicativos do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] também podem ser configurados para proteger as mensagens antes que elas sejam transportadas, usando protocolo WS-Security.</span><span class="sxs-lookup"><span data-stu-id="908aa-330">More important, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] applications can also be configured to secure the messages before they are transported, using the WS-Security protocol.</span></span> <span data-ttu-id="908aa-331">A proteção do corpo de uma mensagem usando o protocolo WS-Security permite que ela seja transmitida confidencialmente através de intermediários antes de chegar ao seu destino final.</span><span class="sxs-lookup"><span data-stu-id="908aa-331">Securing just the body of a message using WS-Security allows it to be transmitted confidentially across intermediaries before reaching its final destination.</span></span>  
  
## <a name="globalization"></a><span data-ttu-id="908aa-332">Globalização</span><span class="sxs-lookup"><span data-stu-id="908aa-332">Globalization</span></span>  
 <span data-ttu-id="908aa-333">O idioma da configuração do ASP.NET permite que você especifique a cultura dos serviços individuais.</span><span class="sxs-lookup"><span data-stu-id="908aa-333">The ASP.NET configuration language allows you to specify the culture for individual services.</span></span> <span data-ttu-id="908aa-334">O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte a essa configuração, a não ser no modo de compatibilidade com o ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="908aa-334">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] does not support that configuration setting except in ASP.NET compatibility mode.</span></span> <span data-ttu-id="908aa-335">Para localizar um serviço do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] que não usa o modo de compatibilidade com o ASP.NET, compile o tipo de serviço em assemblies culturais e tenha pontos de extremidade específicos de cultura separados para cada assembly cultural.</span><span class="sxs-lookup"><span data-stu-id="908aa-335">To localize a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that does not use ASP.NET compatibility mode, compile the service type into culture-specific assemblies, and have separate culture-specific endpoints for each culture-specific assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="908aa-336">Consulte também</span><span class="sxs-lookup"><span data-stu-id="908aa-336">See Also</span></span>  
 [<span data-ttu-id="908aa-337">Comparando serviços Web do ASP.NET ao WCF com base no propósito e padrões usados</span><span class="sxs-lookup"><span data-stu-id="908aa-337">Comparing ASP.NET Web Services to WCF Based on Purpose and Standards Used</span></span>](../../../../docs/framework/wcf/feature-details/comparing-aspnet-web-services-to-wcf-based-on-purpose-and-standards-used.md)
