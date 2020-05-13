---
title: Serialização tolerante a versão
description: O .NET Framework 2,0 apresenta a serialização tolerante a versão, um conjunto de recursos que facilita a modificação de tipos serializáveis.
ms.date: 08/08/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- version tolerant serialization
- serialization, custom serialization
- serialization, version tolerant
- serialization, controlling
- versions and serialization
- BinaryFormatter class, samples
- serialization, attributes
ms.assetid: bea0ffe3-2708-4a16-ac7d-e586ed6b8e8d
ms.openlocfilehash: 87bdc0f0328e7a75477672432c0944818dbef244
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380091"
---
# <a name="version-tolerant-serialization"></a><span data-ttu-id="810bc-103">Serialização tolerante a versão</span><span class="sxs-lookup"><span data-stu-id="810bc-103">Version tolerant serialization</span></span>

<span data-ttu-id="810bc-104">Na versão 1.0 e 1.1 do .NET Framework, criar tipos serializáveis que fossem reutilizáveis de uma versão de um aplicativo para a outra era problemático.</span><span class="sxs-lookup"><span data-stu-id="810bc-104">In version 1.0 and 1.1 of the .NET Framework, creating serializable types that would be reusable from one version of an application to the next was problematic.</span></span> <span data-ttu-id="810bc-105">Se um tipo tivesse sido modificado adicionando campos extras, o seguinte problema ocorreria.</span><span class="sxs-lookup"><span data-stu-id="810bc-105">If a type was modified by adding extra fields, the following problems would occur:</span></span>

- <span data-ttu-id="810bc-106">As versões antigas de um aplicativo gerariam exceções quando fossem solicitadas a desserializar novas versões do tipo antigo.</span><span class="sxs-lookup"><span data-stu-id="810bc-106">Older versions of an application would throw exceptions when asked to deserialize new versions of the old type.</span></span>
- <span data-ttu-id="810bc-107">As versões recentes de um aplicativo gerariam exceções ao desserializar versões antigas de um tipo com dados ausentes.</span><span class="sxs-lookup"><span data-stu-id="810bc-107">Newer versions of an application would throw exceptions when deserializing older versions of a type with missing data.</span></span>

<span data-ttu-id="810bc-108">VTS (Version Tolerant Serialization) é um conjunto de recursos introduzido no .NET Framework 2.0 que facilita, ao longo do tempo, modificar tipos serializáveis.</span><span class="sxs-lookup"><span data-stu-id="810bc-108">Version Tolerant Serialization (VTS) is a set of features introduced in .NET Framework 2.0 that makes it easier, over time, to modify serializable types.</span></span> <span data-ttu-id="810bc-109">Especificamente, os recursos do VTS serão habilitados para classes para as quais o atributo <xref:System.SerializableAttribute> tiver sido aplicado, incluindo tipos genéricos.</span><span class="sxs-lookup"><span data-stu-id="810bc-109">Specifically, the VTS features are enabled for classes to which the <xref:System.SerializableAttribute> attribute has been applied, including generic types.</span></span> <span data-ttu-id="810bc-110">O VTS possibilita adicionar novos campos a essas classes sem interromper a compatibilidade com outras versões do tipo.</span><span class="sxs-lookup"><span data-stu-id="810bc-110">VTS makes it possible to add new fields to those classes without breaking compatibility with other versions of the type.</span></span> <span data-ttu-id="810bc-111">Para obter um aplicativo de exemplo funcional, consulte [Amostra de tecnologia de serialização tolerante a versão](version-tolerant-serialization-technology-sample.md).</span><span class="sxs-lookup"><span data-stu-id="810bc-111">For a working sample application, see [Version Tolerant Serialization Technology Sample](version-tolerant-serialization-technology-sample.md).</span></span>

<span data-ttu-id="810bc-112">Os recursos do VTS são habilitados ao usar o <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span><span class="sxs-lookup"><span data-stu-id="810bc-112">The VTS features are enabled when using the <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>.</span></span> <span data-ttu-id="810bc-113">Além disso, todos os recursos exceto tolerância a dados desconhecidos também são habilitados ao usar o <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span><span class="sxs-lookup"><span data-stu-id="810bc-113">Additionally, all features except extraneous data tolerance are also enabled when using the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>.</span></span> <span data-ttu-id="810bc-114">Para obter mais informações sobre como usar essas classes para serialização, consulte [Serialização binária](binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="810bc-114">For more information about using these classes for serialization, see [Binary Serialization](binary-serialization.md).</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

## <a name="feature-list"></a><span data-ttu-id="810bc-115">Lista de recursos</span><span class="sxs-lookup"><span data-stu-id="810bc-115">Feature list</span></span>

<span data-ttu-id="810bc-116">O conjunto de recursos inclui o seguinte:</span><span class="sxs-lookup"><span data-stu-id="810bc-116">The set of features includes the following:</span></span>

- <span data-ttu-id="810bc-117">Tolerância a dados desconhecidos ou inesperados.</span><span class="sxs-lookup"><span data-stu-id="810bc-117">Tolerance of extraneous or unexpected data.</span></span> <span data-ttu-id="810bc-118">Isso permite que versões mais recentes do tipo enviem dados a versões mais antigas.</span><span class="sxs-lookup"><span data-stu-id="810bc-118">This enables newer versions of the type to send data to older versions.</span></span>
- <span data-ttu-id="810bc-119">Tolerância de dados opcionais ausentes.</span><span class="sxs-lookup"><span data-stu-id="810bc-119">Tolerance of missing optional data.</span></span> <span data-ttu-id="810bc-120">Isso permite que versões mais antigas enviem dados a versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="810bc-120">This enables older versions to send data to newer versions.</span></span>
- <span data-ttu-id="810bc-121">Retornos de chamada de serialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-121">Serialization callbacks.</span></span> <span data-ttu-id="810bc-122">Isso permite a configuração inteligente de valor padrão em casos onde os dados estão ausentes.</span><span class="sxs-lookup"><span data-stu-id="810bc-122">This enables intelligent default value setting in cases where data is missing.</span></span>

<span data-ttu-id="810bc-123">Além disso, há um recurso para declarar quando um novo campo opcional tiver sido adicionado.</span><span class="sxs-lookup"><span data-stu-id="810bc-123">In addition, there is a feature for declaring when a new optional field has been added.</span></span> <span data-ttu-id="810bc-124">Essa é a propriedade <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> do atributo <xref:System.Runtime.Serialization.OptionalFieldAttribute>.</span><span class="sxs-lookup"><span data-stu-id="810bc-124">This is the <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A> property of the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute.</span></span>

<span data-ttu-id="810bc-125">Esses recursos são discutidos mais detalhadamente nas seções a seguir.</span><span class="sxs-lookup"><span data-stu-id="810bc-125">These features are discussed in greater detail in the following sections.</span></span>

### <a name="tolerance-of-extraneous-or-unexpected-data"></a><span data-ttu-id="810bc-126">Tolerância a dados desconhecidos ou inesperados</span><span class="sxs-lookup"><span data-stu-id="810bc-126">Tolerance of extraneous or unexpected data</span></span>

<span data-ttu-id="810bc-127">No passado, durante a desserialização, os dados desconhecidos ou inesperados fizeram exceções serem geradas.</span><span class="sxs-lookup"><span data-stu-id="810bc-127">In the past, during deserialization, any extraneous or unexpected data caused exceptions to be thrown.</span></span> <span data-ttu-id="810bc-128">Com o VTS, na mesma situação, os dados desconhecidos ou inesperados eram ignorados em vez de fazerem exceções serem geradas.</span><span class="sxs-lookup"><span data-stu-id="810bc-128">With VTS, in the same situation, any extraneous or unexpected data is ignored instead of causing exceptions to be thrown.</span></span> <span data-ttu-id="810bc-129">Isso permite que aplicativos que usam versões mais recentes de um tipo (ou seja, uma versão que inclua mais campos) enviem informações para aplicativos que esperam versões mais recentes do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="810bc-129">This enables applications that use newer versions of a type (that is, a version that includes more fields) to send information to applications that expect older versions of the same type.</span></span>

<span data-ttu-id="810bc-130">No exemplo a seguir, os dados extras contidos no `CountryField` da versão 2.0 da classe `Address` são ignorados quando um aplicativo mais antigo desserializa a versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="810bc-130">In the following example, the extra data contained in the `CountryField` of version 2.0 of the `Address` class is ignored when an older application deserializes the newer version.</span></span>

```csharp  
// Version 1 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
}  
// Version 2.0 of the Address class.  
[Serializable]  
public class Address  
{  
    public string Street;  
    public string City;  
    // The older application ignores this data.  
    public string CountryField;  
}  
```  
  
```vb  
' Version 1 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
End Class  
  
' Version 2.0 of the Address class.  
<Serializable> _  
Public Class Address  
    Public Street As String  
    Public City As String  
    ' The older application ignores this data.  
    Public CountryField As String  
End Class  
```  

### <a name="tolerance-of-missing-data"></a><span data-ttu-id="810bc-131">Tolerância de dados ausentes</span><span class="sxs-lookup"><span data-stu-id="810bc-131">Tolerance of missing data</span></span>

<span data-ttu-id="810bc-132">Os campos podem ser marcados como opcionais aplicando o atributo <xref:System.Runtime.Serialization.OptionalFieldAttribute> a eles.</span><span class="sxs-lookup"><span data-stu-id="810bc-132">Fields can be marked as optional by applying the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to them.</span></span> <span data-ttu-id="810bc-133">Durante a desserialização, se os dados opcionais estiverem ausentes, o mecanismo de serialização ignorará a ausência e não gerará uma exceção.</span><span class="sxs-lookup"><span data-stu-id="810bc-133">During deserialization, if the optional data is missing, the serialization engine ignores the absence and does not throw an exception.</span></span> <span data-ttu-id="810bc-134">Assim, os aplicativos que esperam versões mais recentes de um tipo podem enviar dados para aplicativos que esperam versões mais recentes do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="810bc-134">Thus, applications that expect older versions of a type can send data to applications that expect newer versions of the same type.</span></span>

<span data-ttu-id="810bc-135">O exemplo a seguir mostra uma versão 2.0 da classe `Address` com o campo `CountryField` marcado como opcional.</span><span class="sxs-lookup"><span data-stu-id="810bc-135">The following example shows version 2.0 of the `Address` class with the `CountryField` field marked as optional.</span></span> <span data-ttu-id="810bc-136">Se um aplicativo mais antigo enviar a versão 1 para um aplicativo mais recente que espera a versão 2.0, a ausência dos dados será ignorada.</span><span class="sxs-lookup"><span data-stu-id="810bc-136">If an older application sends version 1 to a newer application that expects version 2.0, the absence of the data is ignored.</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;

    [OptionalField]
    public string CountryField;
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String

    <OptionalField> _
    Public CountryField As String
End Class
```
  
### <a name="serialization-callbacks"></a><span data-ttu-id="810bc-137">Retornos de chamada de serialização</span><span class="sxs-lookup"><span data-stu-id="810bc-137">Serialization callbacks</span></span>

<span data-ttu-id="810bc-138">Os retornos de chamada de serialização são um mecanismo que fornece ganchos no processo de serialização/desserialização em quatro pontos.</span><span class="sxs-lookup"><span data-stu-id="810bc-138">Serialization callbacks are a mechanism that provides hooks into the serialization/deserialization process at four points.</span></span>

|<span data-ttu-id="810bc-139">Atributo</span><span class="sxs-lookup"><span data-stu-id="810bc-139">Attribute</span></span>|<span data-ttu-id="810bc-140">Quando o método associado é chamado</span><span class="sxs-lookup"><span data-stu-id="810bc-140">When the Associated Method is Called</span></span>|<span data-ttu-id="810bc-141">Usos comum</span><span class="sxs-lookup"><span data-stu-id="810bc-141">Typical Use</span></span>|
|---------------|------------------------------------------|-----------------|
|<xref:System.Runtime.Serialization.OnDeserializingAttribute>|<span data-ttu-id="810bc-142">Antes da desserialização.\*</span><span class="sxs-lookup"><span data-stu-id="810bc-142">Before deserialization.\*</span></span>|<span data-ttu-id="810bc-143">Inicialize valores padrão para campos opcionais.</span><span class="sxs-lookup"><span data-stu-id="810bc-143">Initialize default values for optional fields.</span></span>|
|<xref:System.Runtime.Serialization.OnDeserializedAttribute>|<span data-ttu-id="810bc-144">Depois da desserialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-144">After deserialization.</span></span>|<span data-ttu-id="810bc-145">Corrija valores de campo opcionais com base nos conteúdos de outros campos.</span><span class="sxs-lookup"><span data-stu-id="810bc-145">Fix optional field values based on contents of other fields.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializingAttribute>|<span data-ttu-id="810bc-146">Antes da serialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-146">Before serialization.</span></span>|<span data-ttu-id="810bc-147">Prepare para a serialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-147">Prepare for serialization.</span></span> <span data-ttu-id="810bc-148">Por exemplo, crie estruturas de dados opcionais.</span><span class="sxs-lookup"><span data-stu-id="810bc-148">For example, create optional data structures.</span></span>|
|<xref:System.Runtime.Serialization.OnSerializedAttribute>|<span data-ttu-id="810bc-149">Depois da serialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-149">After serialization.</span></span>|<span data-ttu-id="810bc-150">Registre os eventos de serialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-150">Log serialization events.</span></span>|

 <span data-ttu-id="810bc-151">\* Esse retorno de chamada é invocado antes do construtor de desserialização, se houver.</span><span class="sxs-lookup"><span data-stu-id="810bc-151">\* This callback is invoked before the deserialization constructor, if one is present.</span></span>

#### <a name="using-callbacks"></a><span data-ttu-id="810bc-152">Usando retornos de chamada</span><span class="sxs-lookup"><span data-stu-id="810bc-152">Using callbacks</span></span>

<span data-ttu-id="810bc-153">Para usar retornos de chamada, aplique o atributo apropriado a um método que aceita um parâmetro <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="810bc-153">To use callbacks, apply the appropriate attribute to a method that accepts a <xref:System.Runtime.Serialization.StreamingContext> parameter.</span></span> <span data-ttu-id="810bc-154">Somente um método por classe pode ser marcado com cada um desses atributos.</span><span class="sxs-lookup"><span data-stu-id="810bc-154">Only one method per class can be marked with each of these attributes.</span></span> <span data-ttu-id="810bc-155">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="810bc-155">For example:</span></span>

```csharp
[OnDeserializing]
private void SetCountryRegionDefault(StreamingContext sc)
{
    CountryField = "Japan";
}
```

```vb
<OnDeserializing>
Private Sub SetCountryRegionDefault(sc As StreamingContext)
    CountryField = "Japan"
End Sub
```

<span data-ttu-id="810bc-156">O uso pretendido desses métodos é para controle de versão.</span><span class="sxs-lookup"><span data-stu-id="810bc-156">The intended use of these methods is for versioning.</span></span> <span data-ttu-id="810bc-157">Durante a desserialização, um campo opcional pode não estar corretamente inicializado se os dados para o campo estiverem ausentes.</span><span class="sxs-lookup"><span data-stu-id="810bc-157">During deserialization, an optional field may not be correctly initialized if the data for the field is missing.</span></span> <span data-ttu-id="810bc-158">Isso pode ser corrigido com a criação do método que atribui o valor correto e, em seguida, com a aplicação do atributo **OnDeserializingAttribute** ou **OnDeserializedAttribute** ao método.</span><span class="sxs-lookup"><span data-stu-id="810bc-158">This can be corrected by creating the method that assigns the correct value, then applying either the **OnDeserializingAttribute** or **OnDeserializedAttribute** attribute to the method.</span></span>

<span data-ttu-id="810bc-159">O exemplo a seguir mostra o método no contexto de um tipo.</span><span class="sxs-lookup"><span data-stu-id="810bc-159">The following example shows the method in the context of a type.</span></span> <span data-ttu-id="810bc-160">Se uma versão anterior de um aplicativo enviar uma instância da classe `Address` para uma versão posterior do aplicativo, os dados do campo `CountryField` ficarão faltando.</span><span class="sxs-lookup"><span data-stu-id="810bc-160">If an earlier version of an application sends an instance of the `Address` class to a later version of the application, the `CountryField` field data will be missing.</span></span> <span data-ttu-id="810bc-161">Mas, após a desserialização, o campo será definido como um valor padrão "Japão".</span><span class="sxs-lookup"><span data-stu-id="810bc-161">But after deserialization, the field will be set to a default value "Japan".</span></span>

```csharp
[Serializable]
public class Address
{
    public string Street;
    public string City;
    [OptionalField]
    public string CountryField;

    [OnDeserializing]
    private void SetCountryRegionDefault(StreamingContext sc)
    {
        CountryField = "Japan";
    }
}
```

```vb
<Serializable> _
Public Class Address
    Public Street As String
    Public City As String
    <OptionalField> _
    Public CountryField As String

    <OnDeserializing> _
    Private Sub SetCountryRegionDefault(sc As StreamingContext)
        CountryField = "Japan"
    End Sub
End Class
```

## <a name="the-versionadded-property"></a><span data-ttu-id="810bc-162">A propriedade VersionAdded</span><span class="sxs-lookup"><span data-stu-id="810bc-162">The VersionAdded property</span></span>

<span data-ttu-id="810bc-163">O **OptionalFieldAttribute** tem a propriedade **VersionAdded**.</span><span class="sxs-lookup"><span data-stu-id="810bc-163">The **OptionalFieldAttribute** has the **VersionAdded** property.</span></span> <span data-ttu-id="810bc-164">Na versão 2.0 do .NET Framework, isso não é usado.</span><span class="sxs-lookup"><span data-stu-id="810bc-164">In version 2.0 of the .NET Framework, this isn't used.</span></span> <span data-ttu-id="810bc-165">No entanto, é importante definir essa propriedade corretamente para verificar se o tipo será compatível com mecanismos de serialização futuros.</span><span class="sxs-lookup"><span data-stu-id="810bc-165">However, it's important to set this property correctly to ensure that the type will be compatible with future serialization engines.</span></span>

<span data-ttu-id="810bc-166">A propriedade indica a qual versão de um tipo um determinado campo foi adicionado.</span><span class="sxs-lookup"><span data-stu-id="810bc-166">The property indicates which version of a type a given field has been added.</span></span> <span data-ttu-id="810bc-167">Ele deve ser incrementado exatamente em um (a partir de 2) a cada vez que o tipo é modificado, conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="810bc-167">It should be incremented by exactly one (starting at 2) every time the type is modified, as shown in the following example:</span></span>

```csharp
// Version 1.0
[Serializable]
public class Person
{
    public string FullName;
}

// Version 2.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded = 2)]
    public string NickName;
    [OptionalField(VersionAdded = 2)]
    public DateTime BirthDate;
}

// Version 3.0
[Serializable]
public class Person
{
    public string FullName;

    [OptionalField(VersionAdded=2)]
    public string NickName;
    [OptionalField(VersionAdded=2)]
    public DateTime BirthDate;

    [OptionalField(VersionAdded=3)]
    public int Weight;
}
```

```vb
' Version 1.0
<Serializable> _
Public Class Person
    Public FullName
End Class

' Version 2.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime
End Class

' Version 3.0
<Serializable> _
Public Class Person
    Public FullName As String

    <OptionalField(VersionAdded := 2)> _
    Public NickName As String
    <OptionalField(VersionAdded := 2)> _
    Public BirthDate As DateTime

    <OptionalField(VersionAdded := 3)> _
    Public Weight As Integer
End Class
```

## <a name="serializationbinder"></a><span data-ttu-id="810bc-168">SerializationBinder</span><span class="sxs-lookup"><span data-stu-id="810bc-168">SerializationBinder</span></span>

<span data-ttu-id="810bc-169">Alguns usuários podem precisar controlar qual classe serializar e desserializar porque uma versão diferente da classe é necessária no servidor e no cliente.</span><span class="sxs-lookup"><span data-stu-id="810bc-169">Some users may need to control which class to serialize and deserialize because a different version of the class is required on the server and client.</span></span> <span data-ttu-id="810bc-170">O <xref:System.Runtime.Serialization.SerializationBinder> é uma classe abstrata usada para controlar os tipos reais usados durante a serialização e a desserialização.</span><span class="sxs-lookup"><span data-stu-id="810bc-170"><xref:System.Runtime.Serialization.SerializationBinder> is an abstract class used to control the actual types used during serialization and deserialization.</span></span> <span data-ttu-id="810bc-171">Para usar essa classe, derive uma classe de <xref:System.Runtime.Serialization.SerializationBinder> e substitua os métodos <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> e <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A>.</span><span class="sxs-lookup"><span data-stu-id="810bc-171">To use this class, derive a class from <xref:System.Runtime.Serialization.SerializationBinder> and override the <xref:System.Runtime.Serialization.SerializationBinder.BindToName%2A> and <xref:System.Runtime.Serialization.SerializationBinder.BindToType%2A> methods.</span></span> <span data-ttu-id="810bc-172">Para obter mais informações, consulte [controlando a serialização e desserialização com o SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span><span class="sxs-lookup"><span data-stu-id="810bc-172">For more information, see [Controlling Serialization and Deserialization with SerializationBinder](../../framework/wcf/feature-details/controlling-serialization-and-deserialization-with-serializationbinder.md).</span></span>

## <a name="best-practices"></a><span data-ttu-id="810bc-173">Práticas recomendadas</span><span class="sxs-lookup"><span data-stu-id="810bc-173">Best practices</span></span>

<span data-ttu-id="810bc-174">Para garantir um comportamento de controle de versão apropriado, siga essas regras ao modificar um tipo de versão para versão:</span><span class="sxs-lookup"><span data-stu-id="810bc-174">To ensure proper versioning behavior, follow these rules when modifying a type from version to version:</span></span>

- <span data-ttu-id="810bc-175">Nunca remova um campo serializado.</span><span class="sxs-lookup"><span data-stu-id="810bc-175">Never remove a serialized field.</span></span>
- <span data-ttu-id="810bc-176">Nunca aplique o atributo <xref:System.NonSerializedAttribute> a um campo se o atributo não tiver sido aplicado ao campo na versão anterior.</span><span class="sxs-lookup"><span data-stu-id="810bc-176">Never apply the <xref:System.NonSerializedAttribute> attribute to a field if the attribute was not applied to the field in the previous version.</span></span>
- <span data-ttu-id="810bc-177">Nunca altere o nome ou o tipo de um campo serializado.</span><span class="sxs-lookup"><span data-stu-id="810bc-177">Never change the name or the type of a serialized field.</span></span>
- <span data-ttu-id="810bc-178">Ao adicionar um novo campo serializado, aplique o atributo **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="810bc-178">When adding a new serialized field, apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="810bc-179">Ao remover um atributo **NonSerializedAttribute** de um campo (que não era serializável em uma versão anterior), aplique o atributo **OptionalFieldAttribute**.</span><span class="sxs-lookup"><span data-stu-id="810bc-179">When removing a **NonSerializedAttribute** attribute from a field (that was not serializable in a previous version), apply the **OptionalFieldAttribute** attribute.</span></span>
- <span data-ttu-id="810bc-180">Para todos os campos opcionais, defina padrões significativos usando os retornos de chamada de serialização, a menos que 0 ou **null** sejam aceitáveis como padrões.</span><span class="sxs-lookup"><span data-stu-id="810bc-180">For all optional fields, set meaningful defaults using the serialization callbacks unless 0 or **null** as defaults are acceptable.</span></span>

<span data-ttu-id="810bc-181">Para definir que um tipo seja compatível com mecanismos de serialização futuros, siga essas diretrizes:</span><span class="sxs-lookup"><span data-stu-id="810bc-181">To ensure that a type will be compatible with future serialization engines, follow these guidelines:</span></span>

- <span data-ttu-id="810bc-182">Sempre defina a propriedade **VersionAdded** no atributo **OptionalFieldAttribute** corretamente.</span><span class="sxs-lookup"><span data-stu-id="810bc-182">Always set the **VersionAdded** property on the **OptionalFieldAttribute** attribute correctly.</span></span>
- <span data-ttu-id="810bc-183">Evite controle de versão ramificado.</span><span class="sxs-lookup"><span data-stu-id="810bc-183">Avoid branched versioning.</span></span>

## <a name="see-also"></a><span data-ttu-id="810bc-184">Confira também</span><span class="sxs-lookup"><span data-stu-id="810bc-184">See also</span></span>

- <xref:System.SerializableAttribute>
- <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>
- <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute.VersionAdded%2A>
- <xref:System.Runtime.Serialization.OptionalFieldAttribute>
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>
- <xref:System.Runtime.Serialization.OnSerializingAttribute>
- <xref:System.Runtime.Serialization.OnSerializedAttribute>
- <xref:System.Runtime.Serialization.StreamingContext>
- <xref:System.NonSerializedAttribute>
- [<span data-ttu-id="810bc-185">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="810bc-185">Binary Serialization</span></span>](binary-serialization.md)
