---
title: Referências de objeto
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5ac8eba44168befae92bef30a054c00d997cc54b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965606"
---
# <a name="object-references"></a><span data-ttu-id="bdd50-102">Referências de objeto</span><span class="sxs-lookup"><span data-stu-id="bdd50-102">Object References</span></span>
<span data-ttu-id="bdd50-103">Este exemplo demonstra como passar objetos por referências entre servidor e cliente.</span><span class="sxs-lookup"><span data-stu-id="bdd50-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="bdd50-104">O exemplo usa *redes sociais*simuladas.</span><span class="sxs-lookup"><span data-stu-id="bdd50-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="bdd50-105">Uma rede social consiste em uma `Person` classe que contém uma lista de amigos em que cada amigo é uma instância `Person` da classe, com sua própria lista de amigos.</span><span class="sxs-lookup"><span data-stu-id="bdd50-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="bdd50-106">Isso cria um grafo de objetos.</span><span class="sxs-lookup"><span data-stu-id="bdd50-106">This creates a graph of objects.</span></span> <span data-ttu-id="bdd50-107">O serviço expõe operações nessas redes sociais.</span><span class="sxs-lookup"><span data-stu-id="bdd50-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="bdd50-108">Neste exemplo, o serviço é hospedado pelo Serviços de Informações da Internet (IIS) e o cliente é um aplicativo de console (. exe).</span><span class="sxs-lookup"><span data-stu-id="bdd50-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdd50-109">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="bdd50-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="bdd50-110">Serviço</span><span class="sxs-lookup"><span data-stu-id="bdd50-110">Service</span></span>  
 <span data-ttu-id="bdd50-111">A `Person` classe tem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo aplicado, `true` com o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> campo definido como para declará-lo como um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="bdd50-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="bdd50-112">Todas as propriedades têm <xref:System.Runtime.Serialization.DataMemberAttribute> o atributo aplicado.</span><span class="sxs-lookup"><span data-stu-id="bdd50-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```csharp
[DataContract(IsReference=true)]  
public class Person  
{  
    string name;  
    string location;  
    string gender;  
    int age;  
    List<Person> friends;  
    [DataMember()]  
    public string Name  
    {  
        get { return name; }  
        set { name = value; }  
    }  
    [DataMember()]  
    public string Location  
    {  
        get { return location; }  
        set { location = value; }  
    }  
    [DataMember()]  
    public string Gender  
    {  
        get { return gender; }  
        set { gender = value; }  
    }  
…  
}  
```  
  
 <span data-ttu-id="bdd50-113">A `GetPeopleInNetwork` operação usa um parâmetro do tipo `Person` e retorna todas as pessoas na rede, ou seja, `friends` todas as pessoas na lista, os amigos do amigo e assim por diante, sem duplicatas.</span><span class="sxs-lookup"><span data-stu-id="bdd50-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="bdd50-114">A `GetMutualFriends` operação usa um parâmetro do tipo `Person` e retorna todos os amigos na lista que também `friends` têm essa pessoa na lista.</span><span class="sxs-lookup"><span data-stu-id="bdd50-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```csharp
public List<Person> GetMutualFriends(Person p)  
{  
    List<Person> mutual = new List<Person>();  
    foreach (Person friend in p.Friends)  
    {  
        if (friend.Friends.Contains(p))  
            mutual.Add(friend);  
    }  
    return mutual;  
}  
```  
  
 <span data-ttu-id="bdd50-115">A `GetCommonFriends` operação usa uma lista do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="bdd50-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="bdd50-116">Espera-se que a lista tenha `Person` dois objetos.</span><span class="sxs-lookup"><span data-stu-id="bdd50-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="bdd50-117">A operação retorna uma lista de `Person` objetos que estão `friends` nas listas de ambos os `Person` objetos na lista de entrada.</span><span class="sxs-lookup"><span data-stu-id="bdd50-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```csharp
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="bdd50-118">Cliente</span><span class="sxs-lookup"><span data-stu-id="bdd50-118">Client</span></span>  
 <span data-ttu-id="bdd50-119">O proxy do cliente é criado usando o recurso **Adicionar referência de serviço** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bdd50-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="bdd50-120">Uma rede social que consiste em cinco `Person` objetos é criada.</span><span class="sxs-lookup"><span data-stu-id="bdd50-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="bdd50-121">O cliente chama cada um dos três métodos no serviço.</span><span class="sxs-lookup"><span data-stu-id="bdd50-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="bdd50-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="bdd50-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="bdd50-123">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bdd50-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="bdd50-124">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bdd50-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="bdd50-125">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="bdd50-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bdd50-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bdd50-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="bdd50-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bdd50-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bdd50-128">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="bdd50-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bdd50-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bdd50-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="bdd50-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bdd50-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="bdd50-131">Referências de objeto interoperável</span><span class="sxs-lookup"><span data-stu-id="bdd50-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
