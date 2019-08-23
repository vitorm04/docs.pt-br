---
title: Serialização personalizada
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- binary serialization, custom serialization
- custom serialization
- binary serialization, controlling
- OptionalFieldAttribute class, custom serialization
- ISerializable interface, custom serialization
- OnDeserializingAttribute class, custom serialization
- OnSerializedAttribute class, custom serialization
- serialization, custom serialization
- serialization, controlling
- OnDeserializedAttribute class, custom serialization
- OnSerializingAttribute class, custom serialization
ms.assetid: 12ed422d-5280-49b8-9b71-a2ed129c0384
ms.openlocfilehash: bd0010ccd3c7f6b2f4433fe8ce234bc806754260
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69916236"
---
# <a name="custom-serialization"></a><span data-ttu-id="e6680-102">Serialização personalizada</span><span class="sxs-lookup"><span data-stu-id="e6680-102">Custom serialization</span></span>
<span data-ttu-id="e6680-103">A serialização personalizada é o processo de controlar a serialização e a desserialização de um tipo.</span><span class="sxs-lookup"><span data-stu-id="e6680-103">Custom serialization is the process of controlling the serialization and deserialization of a type.</span></span> <span data-ttu-id="e6680-104">Controlando a serialização, é possível garantir a compatibilidade de serialização, que é a capacidade de serializar e desserializar entre versões de um tipo sem interromper a funcionalidade básica do tipo.</span><span class="sxs-lookup"><span data-stu-id="e6680-104">By controlling serialization, it's possible to ensure serialization compatibility, which is the ability to serialize and deserialize between versions of a type without breaking the core functionality of the type.</span></span> <span data-ttu-id="e6680-105">Por exemplo, na primeira versão de um tipo, pode haver apenas dois campos.</span><span class="sxs-lookup"><span data-stu-id="e6680-105">For example, in the first version of a type, there may be only two fields.</span></span> <span data-ttu-id="e6680-106">Na próxima versão de um tipo, vários outros campos são adicionados.</span><span class="sxs-lookup"><span data-stu-id="e6680-106">In the next version of a type, several more fields are added.</span></span> <span data-ttu-id="e6680-107">No entanto, a segunda versão de um aplicativo deve ser capaz de serializar e desserializar ambos os tipos.</span><span class="sxs-lookup"><span data-stu-id="e6680-107">Yet the second version of an application must be able to serialize and deserialize both types.</span></span> <span data-ttu-id="e6680-108">As seções a seguir descrevem como controlar a serialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-108">The following sections describe how to control serialization.</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
> [!IMPORTANT]
> <span data-ttu-id="e6680-109">Nas versões anteriores ao .NET Framework 4.0, a serialização de dados personalizados do usuário em um assembly parcialmente confiável era realizada com o GetObjectData.</span><span class="sxs-lookup"><span data-stu-id="e6680-109">In versions previous to .NET Framework 4.0, serialization of custom user data in a partially trusted assembly was accomplished using the GetObjectData.</span></span> <span data-ttu-id="e6680-110">Iniciando com a versão 4.0, esse método é marcado com o atributo <xref:System.Security.SecurityCriticalAttribute> que impede a execução em assemblies parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="e6680-110">Starting with version 4.0, that method is marked with the <xref:System.Security.SecurityCriticalAttribute> attribute which prevents execution in partially trusted assemblies.</span></span> <span data-ttu-id="e6680-111">Para contornar esta condição, implemente a interface <xref:System.Runtime.Serialization.ISafeSerializationData>.</span><span class="sxs-lookup"><span data-stu-id="e6680-111">To work around this condition, implement the <xref:System.Runtime.Serialization.ISafeSerializationData> interface.</span></span>  
  
## <a name="running-custom-methods-during-and-after-serialization"></a><span data-ttu-id="e6680-112">Executando métodos personalizados durante e após a serialização</span><span class="sxs-lookup"><span data-stu-id="e6680-112">Running custom methods during and after serialization</span></span>  
 <span data-ttu-id="e6680-113">A prática recomendada e a maneira mais fácil (introduzidas na versão 2.0 do .NET Framework) é aplicar os seguintes atributos a métodos que são usados para corrigir dados durante e após a serialização:</span><span class="sxs-lookup"><span data-stu-id="e6680-113">The best practice and easiest way (introduced in version 2.0 of the .NET Framework) is to apply the following attributes to methods that are used to correct data during and after serialization:</span></span>  
  
- <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
- <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
 <span data-ttu-id="e6680-114">Esses atributos permitem que o tipo participe de qualquer uma ou todas as quatro fases dos processos de serialização e desserialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-114">These attributes allow the type to participate in any one of, or all four of the phases, of the serialization and deserialization processes.</span></span> <span data-ttu-id="e6680-115">Os atributos especificam os métodos do tipo que devem ser chamados durante cada fase.</span><span class="sxs-lookup"><span data-stu-id="e6680-115">The attributes specify the methods of the type that should be invoked during each phase.</span></span> <span data-ttu-id="e6680-116">Os métodos não acessam o fluxo de serialização. Em vez disso, permitem alterar o objeto antes e depois da serialização, ou antes e depois da desserialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-116">The methods do not access the serialization stream but instead allow you to alter the object before and after serialization, or before and after deserialization.</span></span> <span data-ttu-id="e6680-117">Os atributos podem ser aplicados a todos os níveis da hierarquia de herança do tipo e cada método é chamado na hierarquia da base para a mais derivada.</span><span class="sxs-lookup"><span data-stu-id="e6680-117">The attributes can be applied at all levels of the type inheritance hierarchy, and each method is called in the hierarchy from the base to the most derived.</span></span> <span data-ttu-id="e6680-118">Esse mecanismo impede a complexidade e os problemas resultantes de se implementar a interface <xref:System.Runtime.Serialization.ISerializable> dando a responsabilidade para serialização e desserialização à implementação mais derivada.</span><span class="sxs-lookup"><span data-stu-id="e6680-118">This mechanism avoids the complexity and any resulting issues of implementing the <xref:System.Runtime.Serialization.ISerializable> interface by giving the responsibility for serialization and deserialization to the most derived implementation.</span></span> <span data-ttu-id="e6680-119">Além disso, esse mecanismo permite que os formatadores ignorem a população de campos e de recuperação do fluxo de serialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-119">Additionally, this mechanism allows the formatters to ignore the population of fields and retrieval from the serialization stream.</span></span> <span data-ttu-id="e6680-120">Para obter detalhes e exemplos de controle de serialização e desserialização, clique em um dos links anteriores.</span><span class="sxs-lookup"><span data-stu-id="e6680-120">For details and examples of controlling serialization and deserialization, click any of the previous links.</span></span>  
  
 <span data-ttu-id="e6680-121">Além disso, ao adicionar um novo campo a um tipo serializável existente, aplique o atributo <xref:System.Runtime.Serialization.OptionalFieldAttribute> ao campo.</span><span class="sxs-lookup"><span data-stu-id="e6680-121">In addition, when adding a new field to an existing serializable type, apply the <xref:System.Runtime.Serialization.OptionalFieldAttribute> attribute to the field.</span></span> <span data-ttu-id="e6680-122"><xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> e <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignoram a ausência do campo quando um fluxo que não tem o novo campo é processado.</span><span class="sxs-lookup"><span data-stu-id="e6680-122">The <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> and the <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> ignores the absence of the field when a stream that is missing the new field is processed.</span></span>  
  
## <a name="implementing-the-iserializable-interface"></a><span data-ttu-id="e6680-123">Implementando a interface ISerializable</span><span class="sxs-lookup"><span data-stu-id="e6680-123">Implementing the ISerializable interface</span></span>  
 <span data-ttu-id="e6680-124">A outra maneira de controlar a serialização é obtida pela implementação da interface <xref:System.Runtime.Serialization.ISerializable> em um objeto.</span><span class="sxs-lookup"><span data-stu-id="e6680-124">The other way to control serialization is achieved by implementing the <xref:System.Runtime.Serialization.ISerializable> interface on an object.</span></span> <span data-ttu-id="e6680-125">Observe, no entanto, que o método na seção anterior substitui esse método para controlar a serialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-125">Note, however, that the method in the previous section supersedes this method to control serialization.</span></span>  
  
 <span data-ttu-id="e6680-126">Além disso, você não deve usar a serialização padrão em uma classe que está marcada com o atributo [Serializable](xref:System.SerializableAttribute) e que tem segurança declarativa ou imperativa no nível da classe ou em seus construtores.</span><span class="sxs-lookup"><span data-stu-id="e6680-126">In addition, you should not use default serialization on a class that is marked with the [Serializable](xref:System.SerializableAttribute) attribute and has declarative or imperative security at the class level or on its constructors.</span></span> <span data-ttu-id="e6680-127">Em vez disso, essas classes sempre devem implementar a interface <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="e6680-127">Instead, these classes should always implement the <xref:System.Runtime.Serialization.ISerializable> interface.</span></span>  
  
 <span data-ttu-id="e6680-128">A implementação de <xref:System.Runtime.Serialization.ISerializable> envolve a implementação do método `GetObjectData` e um construtor especial que é usado quando o objeto é desserializado.</span><span class="sxs-lookup"><span data-stu-id="e6680-128">Implementing <xref:System.Runtime.Serialization.ISerializable> involves implementing the `GetObjectData` method and a special constructor that is used when the object is deserialized.</span></span> <span data-ttu-id="e6680-129">O código de exemplo a seguir mostra como implementar <xref:System.Runtime.Serialization.ISerializable> na classe `MyObject` de uma seção anterior.</span><span class="sxs-lookup"><span data-stu-id="e6680-129">The following sample code shows how to implement <xref:System.Runtime.Serialization.ISerializable> on the `MyObject` class from a previous section.</span></span>  
  
```csharp
[Serializable]
public class MyObject : ISerializable
{
    public int n1;
    public int n2;
    public String str;

    public MyObject()
    {
    }

    protected MyObject(SerializationInfo info, StreamingContext context)
    {
      n1 = info.GetInt32("i");
      n2 = info.GetInt32("j");
      str = info.GetString("k");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public virtual void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        info.AddValue("i", n1);
        info.AddValue("j", n2);
        info.AddValue("k", str);
    }
}
```

```vb
<Serializable()>  _
Public Class MyObject
    Implements ISerializable
    Public n1 As Integer
    Public n2 As Integer
    Public str As String

    Public Sub New()
    End Sub

    Protected Sub New(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        n1 = info.GetInt32("i")
        n2 = info.GetInt32("j")
        str = info.GetString("k")
    End Sub 'New

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overridable Sub GetObjectData(ByVal info As SerializationInfo, ByVal context As StreamingContext)
        info.AddValue("i", n1)
        info.AddValue("j", n2)
        info.AddValue("k", str)
    End Sub
End Class
```  
  
 <span data-ttu-id="e6680-130">Quando **GetObjectData** é chamado durante a serialização, você é responsável por popular as <xref:System.Runtime.Serialization.SerializationInfo> fornecidas com a chamada de método.</span><span class="sxs-lookup"><span data-stu-id="e6680-130">When **GetObjectData** is called during serialization, you are responsible for populating the <xref:System.Runtime.Serialization.SerializationInfo> provided with the method call.</span></span> <span data-ttu-id="e6680-131">Adicione as variáveis a serem serializadas como pares de nome e valor.</span><span class="sxs-lookup"><span data-stu-id="e6680-131">Add the variables to be serialized as name and value pairs.</span></span> <span data-ttu-id="e6680-132">Qualquer texto pode ser usado como o nome.</span><span class="sxs-lookup"><span data-stu-id="e6680-132">Any text can be used as the name.</span></span> <span data-ttu-id="e6680-133">Você tem a liberdade para decidir quais variáveis de membro serão adicionadas às <xref:System.Runtime.Serialization.SerializationInfo>, desde que os dados suficientes sejam serializados para restaurar o objeto durante a desserialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-133">You have the freedom to decide which member variables are added to the <xref:System.Runtime.Serialization.SerializationInfo>, provided that sufficient data is serialized to restore the object during deserialization.</span></span> <span data-ttu-id="e6680-134">As classes derivadas deverão chamar o método **GetObjectData** no objeto base se o último implementar <xref:System.Runtime.Serialization.ISerializable>.</span><span class="sxs-lookup"><span data-stu-id="e6680-134">Derived classes should call the **GetObjectData** method on the base object if the latter implements <xref:System.Runtime.Serialization.ISerializable>.</span></span>  
  
 <span data-ttu-id="e6680-135">Observe que a serialização pode permitir que outro código veja ou modifique os dados da instância de objeto que estejam de outra forma inacessíveis.</span><span class="sxs-lookup"><span data-stu-id="e6680-135">Note that serialization can allow other code to see or modify object instance data that is otherwise inaccessible.</span></span> <span data-ttu-id="e6680-136">Portanto, o código que executa a serialização exige a [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) com o sinalizador <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> especificado.</span><span class="sxs-lookup"><span data-stu-id="e6680-136">Therefore, code that performs serialization requires the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified.</span></span> <span data-ttu-id="e6680-137">De acordo com a política padrão, essa permissão não é dada ao código da intranet ou baixado da Internet; somente o código no computador local recebe essa permissão.</span><span class="sxs-lookup"><span data-stu-id="e6680-137">Under default policy, this permission is not given to Internet-downloaded or intranet code; only code on the local computer is granted this permission.</span></span> <span data-ttu-id="e6680-138">O método **GetObjectData** deve ser explicitamente protegido por meio da exigência de [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) com o sinalizador <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> especificado ou de outras permissões que especificamente ajudam a proteger dados particulares.</span><span class="sxs-lookup"><span data-stu-id="e6680-138">The **GetObjectData** method must be explicitly protected either by demanding the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified or by demanding other permissions that specifically help protect private data.</span></span>  
  
 <span data-ttu-id="e6680-139">Se um campo particular armazenar informações confidenciais, você deverá exigir as permissões apropriadas no **GetObjectData** para proteger os dados.</span><span class="sxs-lookup"><span data-stu-id="e6680-139">If a private field stores sensitive information, you should demand the appropriate permissions on **GetObjectData** to protect the data.</span></span> <span data-ttu-id="e6680-140">Lembre-se de que o código que recebeu a [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) com o sinalizador **SerializationFormatter** especificado pode exibir e modificar os dados armazenados em campos particulares.</span><span class="sxs-lookup"><span data-stu-id="e6680-140">Remember that code that has been granted [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the **SerializationFormatter** flag specified can view and modify the data stored in private fields.</span></span> <span data-ttu-id="e6680-141">Um chamador mal-intencionado que recebeu esta [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) pode exibir dados, como locais de diretório ocultos ou permissões concedidas, e usar os dados para explorar uma vulnerabilidade de segurança no computador.</span><span class="sxs-lookup"><span data-stu-id="e6680-141">A malicious caller granted this [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) can view data such as hidden directory locations or granted permissions and use the data to exploit a security vulnerability on the computer.</span></span> <span data-ttu-id="e6680-142">Para obter uma lista completa dos sinalizadores de permissões de segurança que podem ser especificados, consulte a [Enumeração SecurityPermissionFlag](xref:System.Security.Permissions.SecurityPermissionFlag).</span><span class="sxs-lookup"><span data-stu-id="e6680-142">For a complete list of the security permission flags you can specify, see the [SecurityPermissionFlag Enumeration](xref:System.Security.Permissions.SecurityPermissionFlag).</span></span>  
  
 <span data-ttu-id="e6680-143">É importante ressaltar que, quando <xref:System.Runtime.Serialization.ISerializable> é adicionado a uma classe, é necessário implementar **GetObjectData** e o construtor especial.</span><span class="sxs-lookup"><span data-stu-id="e6680-143">It's important to stress that when <xref:System.Runtime.Serialization.ISerializable> is added to a class you must implement both **GetObjectData** and the special constructor.</span></span> <span data-ttu-id="e6680-144">O compilador avisa se **GetObjectData** está ausente.</span><span class="sxs-lookup"><span data-stu-id="e6680-144">The compiler warns you if **GetObjectData** is missing.</span></span> <span data-ttu-id="e6680-145">No entanto, como é impossível impor a implementação de um construtor, nenhum aviso será fornecido se o construtor estiver ausente, e uma exceção é gerada quando é feita uma tentativa de desserializar uma classe sem o construtor.</span><span class="sxs-lookup"><span data-stu-id="e6680-145">However, because it is impossible to enforce the implementation of a constructor, no warning is provided if the constructor is absent, and an exception is thrown when an attempt is made to deserialize a class without the constructor.</span></span>  
  
 <span data-ttu-id="e6680-146">O projeto atual foi favorecido em relação a um método <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> para solucionar possíveis problemas de segurança e controle de versão.</span><span class="sxs-lookup"><span data-stu-id="e6680-146">The current design was favored above a <xref:System.Runtime.Serialization.ISerializationSurrogate.SetObjectData%2A> method to get around potential security and versioning problems.</span></span> <span data-ttu-id="e6680-147">Por exemplo, um método `SetObjectData` deverá ser público se estiver definido como parte de uma interface; portanto, os usuários devem escrever o código para impedir que o método **SetObjectData** seja chamado várias vezes.</span><span class="sxs-lookup"><span data-stu-id="e6680-147">For example, a `SetObjectData` method must be public if it is defined as part of an interface; thus users must write code to defend against having the **SetObjectData** method called multiple times.</span></span> <span data-ttu-id="e6680-148">Caso contrário, um aplicativo mal-intencionado que chama o método **SetObjectData** em um objeto durante a execução de uma operação poderá causar problemas potenciais.</span><span class="sxs-lookup"><span data-stu-id="e6680-148">Otherwise, a malicious application that calls the **SetObjectData** method on an object in the process of executing an operation can cause potential problems.</span></span>  
  
 <span data-ttu-id="e6680-149">Durante a desserialização, <xref:System.Runtime.Serialization.SerializationInfo> é passado para a classe usando o construtor fornecido para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="e6680-149">During deserialization, <xref:System.Runtime.Serialization.SerializationInfo> is passed to the class using the constructor provided for this purpose.</span></span> <span data-ttu-id="e6680-150">Todas as restrições de visibilidade colocadas no construtor são ignorados quando o objeto é desserializado; assim você pode marcar a classe como pública, protegida, interna ou privada.</span><span class="sxs-lookup"><span data-stu-id="e6680-150">Any visibility constraints placed on the constructor are ignored when the object is deserialized; so you can mark the class as public, protected, internal, or private.</span></span> <span data-ttu-id="e6680-151">No entanto, é uma prática recomendada marcar o construtor como protegido a menos que a classe seja fechada; nesse caso, o construtor é marcado particular.</span><span class="sxs-lookup"><span data-stu-id="e6680-151">However, it is a best practice to make the constructor protected unless the class is sealed, in which case the constructor should be marked private.</span></span> <span data-ttu-id="e6680-152">O construtor também deve executar a validação completa de entrada.</span><span class="sxs-lookup"><span data-stu-id="e6680-152">The constructor should also perform thorough input validation.</span></span> <span data-ttu-id="e6680-153">Para evitar o uso indevido pelo código mal-intencionado, o construtor deve aplicar as mesmas verificações de segurança e permissões necessárias para obter uma instância da classe usando qualquer outro construtor.</span><span class="sxs-lookup"><span data-stu-id="e6680-153">To avoid misuse by malicious code, the constructor should enforce the same security checks and permissions required to obtain an instance of the class using any other constructor.</span></span> <span data-ttu-id="e6680-154">Se você não seguir essa recomendação, o código mal-intencionado poderá pré-serializar um objeto, obter o controle com a [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) com o sinalizador <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> especificado e desserializar o objeto em um computador cliente, ignorando qualquer segurança que tenha sido aplicada durante a construção de instância padrão com um construtor público.</span><span class="sxs-lookup"><span data-stu-id="e6680-154">If you do not follow this recommendation, malicious code can preserialize an object, obtain control with the [SecurityPermission](xref:System.Security.Permissions.SecurityPermissionAttribute) with the <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter> flag specified and deserialize the object on a client computer bypassing any security that would have been applied during standard instance construction using a public constructor.</span></span>  
  
 <span data-ttu-id="e6680-155">Para restaurar o estado do objeto, basta recuperar os valores das variáveis de <xref:System.Runtime.Serialization.SerializationInfo> usando os nomes usados durante a serialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-155">To restore the state of the object, simply retrieve the values of the variables from <xref:System.Runtime.Serialization.SerializationInfo> using the names used during serialization.</span></span> <span data-ttu-id="e6680-156">Se a classe base implementar o <xref:System.Runtime.Serialization.ISerializable>, o construtor de base deverá ser chamado para permitir que o objeto base restaure suas variáveis.</span><span class="sxs-lookup"><span data-stu-id="e6680-156">If the base class implements <xref:System.Runtime.Serialization.ISerializable>, the base constructor should be called to allow the base object to restore its variables.</span></span>  
  
 <span data-ttu-id="e6680-157">Quando você derivar uma nova classe de uma que implementa <xref:System.Runtime.Serialization.ISerializable>, a classe derivada deverá implementar o construtor, bem como o método **GetObjectData**, se tiver variáveis que precisam ser serializadas.</span><span class="sxs-lookup"><span data-stu-id="e6680-157">When you derive a new class from one that implements <xref:System.Runtime.Serialization.ISerializable>, the derived class must implement both the constructor as well as the **GetObjectData** method if it has variables that need to be serialized.</span></span> <span data-ttu-id="e6680-158">O exemplo de código a seguir mostra como isso é feito usando a classe `MyObject` mostrada anteriormente.</span><span class="sxs-lookup"><span data-stu-id="e6680-158">The following code example shows how this is done using the `MyObject` class shown previously.</span></span>  
  
```csharp
[Serializable]
public class ObjectTwo : MyObject
{
    public int num;

    public ObjectTwo()
      : base()
    {
    }

    protected ObjectTwo(SerializationInfo si, StreamingContext context)
      : base(si, context)
    {
        num = si.GetInt32("num");
    }

    [SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter = true)]
    public override void GetObjectData(SerializationInfo si, StreamingContext context)
    {
        base.GetObjectData(si,context);
        si.AddValue("num", num);
    }
}
```

```vb
<Serializable()>  _
Public Class ObjectTwo
    Inherits MyObject
    Public num As Integer

    Public Sub New()

    End Sub

    Protected Sub New(ByVal si As SerializationInfo, _
    ByVal context As StreamingContext)
        MyBase.New(si, context)
        num = si.GetInt32("num")
    End Sub

    <SecurityPermissionAttribute(SecurityAction.Demand, SerializationFormatter := True)> _
    Public Overrides Sub GetObjectData(ByVal si As SerializationInfo, ByVal context As StreamingContext)
        MyBase.GetObjectData(si, context)
        si.AddValue("num", num)
    End Sub
End Class
```  
  
 <span data-ttu-id="e6680-159">Não se esqueça de chamar a classe base no construtor de desserialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-159">Don't forget to call the base class in the deserialization constructor.</span></span> <span data-ttu-id="e6680-160">Se isso não for feito, o construtor na classe base nunca será chamado e o objeto não será totalmente construído após a desserialização.</span><span class="sxs-lookup"><span data-stu-id="e6680-160">If this isn't done, the constructor on the base class is never called, and the object is not fully constructed after deserialization.</span></span>  
  
 <span data-ttu-id="e6680-161">Os objetos são recriados de dentro para fora; e os métodos de chamada durante a desserialização podem ter efeitos colaterais indesejáveis, porque os métodos chamados podem se referir a referências de objeto que não foram desserializados no momento em que a chamada foi feita.</span><span class="sxs-lookup"><span data-stu-id="e6680-161">Objects are reconstructed from the inside out; and calling methods during deserialization can have undesirable side effects, because the methods called might refer to object references that have not been deserialized by the time the call is made.</span></span> <span data-ttu-id="e6680-162">Se a classe que está sendo desserializada implementar o <xref:System.Runtime.Serialization.IDeserializationCallback>, o método <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> será chamado automaticamente quando o gráfico do objeto inteiro tiver sido desserializado.</span><span class="sxs-lookup"><span data-stu-id="e6680-162">If the class being deserialized implements the <xref:System.Runtime.Serialization.IDeserializationCallback>, the <xref:System.Runtime.Serialization.IDeserializationCallback.OnDeserialization*> method is automatically called when the entire object graph has been deserialized.</span></span> <span data-ttu-id="e6680-163">Neste ponto, todos os objetos filho referenciados foram restaurados totalmente.</span><span class="sxs-lookup"><span data-stu-id="e6680-163">At this point, all the child objects referenced have been fully restored.</span></span> <span data-ttu-id="e6680-164">Uma tabela de hash é um exemplo típico de uma classe que é difícil desserializar sem usar a escuta de eventos.</span><span class="sxs-lookup"><span data-stu-id="e6680-164">A hash table is a typical example of a class that is difficult to deserialize without using the event listener.</span></span> <span data-ttu-id="e6680-165">É fácil recuperar os pares de chave e valor durante a desserialização, mas adicionar esses objetos de volta à tabela de hash pode causar problemas, porque não há nenhuma garantia de que as classes que derivaram da tabela de hash foram desserializadas.</span><span class="sxs-lookup"><span data-stu-id="e6680-165">It is easy to retrieve the key and value pairs during deserialization, but adding these objects back to the hash table can cause problems, because there is no guarantee that classes that derived from the hash table have been deserialized.</span></span> <span data-ttu-id="e6680-166">Os métodos de chamada em uma tabela de hash nesse estágio são, portanto, não aconselháveis.</span><span class="sxs-lookup"><span data-stu-id="e6680-166">Calling methods on a hash table at this stage is therefore not advisable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6680-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6680-167">See also</span></span>

- [<span data-ttu-id="e6680-168">Serialização binária</span><span class="sxs-lookup"><span data-stu-id="e6680-168">Binary Serialization</span></span>](binary-serialization.md)
- [<span data-ttu-id="e6680-169">Serialização XML e SOAP</span><span class="sxs-lookup"><span data-stu-id="e6680-169">XML and SOAP Serialization</span></span>](xml-and-soap-serialization.md)
- [<span data-ttu-id="e6680-170">Segurança e serialização</span><span class="sxs-lookup"><span data-stu-id="e6680-170">Security and Serialization</span></span>](../../../docs/framework/misc/security-and-serialization.md)
