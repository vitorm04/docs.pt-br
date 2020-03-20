---
title: Referências de objeto
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 5eb842e1bff9ba60074379fde5ef3d0597f2184e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183454"
---
# <a name="object-references"></a><span data-ttu-id="04adc-102">Referências de objeto</span><span class="sxs-lookup"><span data-stu-id="04adc-102">Object References</span></span>
<span data-ttu-id="04adc-103">Esta amostra demonstra como passar objetos por referências entre servidor e cliente.</span><span class="sxs-lookup"><span data-stu-id="04adc-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="04adc-104">A amostra usa *redes sociais*simuladas.</span><span class="sxs-lookup"><span data-stu-id="04adc-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="04adc-105">Uma rede social consiste `Person` em uma classe que contém uma lista de `Person` amigos em que cada amigo é uma instância da classe, com sua própria lista de amigos.</span><span class="sxs-lookup"><span data-stu-id="04adc-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="04adc-106">Isso cria um gráfico de objetos.</span><span class="sxs-lookup"><span data-stu-id="04adc-106">This creates a graph of objects.</span></span> <span data-ttu-id="04adc-107">O serviço expõe as operações nessas redes sociais.</span><span class="sxs-lookup"><span data-stu-id="04adc-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="04adc-108">Nesta amostra, o serviço é hospedado pelo Internet Information Services (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="04adc-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04adc-109">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="04adc-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="04adc-110">Serviço</span><span class="sxs-lookup"><span data-stu-id="04adc-110">Service</span></span>  
 <span data-ttu-id="04adc-111">A `Person` classe <xref:System.Runtime.Serialization.DataContractAttribute> tem o atributo <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> aplicado, `true` com o campo definido para declará-lo como um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="04adc-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="04adc-112">Todas as <xref:System.Runtime.Serialization.DataMemberAttribute> propriedades têm o atributo aplicado.</span><span class="sxs-lookup"><span data-stu-id="04adc-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
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
  
 <span data-ttu-id="04adc-113">A `GetPeopleInNetwork` operação tem um `Person` parâmetro de tipo e devolve todas as pessoas da rede; ou seja, todas as `friends` pessoas da lista, os amigos do amigo, e assim por diante, sem duplicatas.</span><span class="sxs-lookup"><span data-stu-id="04adc-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```csharp
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="04adc-114">A `GetMutualFriends` operação tem um `Person` parâmetro de tipo e devolve todos os amigos `friends` da lista que também têm essa pessoa em sua lista.</span><span class="sxs-lookup"><span data-stu-id="04adc-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
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
  
 <span data-ttu-id="04adc-115">A `GetCommonFriends` operação leva uma `Person`lista de tipos.</span><span class="sxs-lookup"><span data-stu-id="04adc-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="04adc-116">Espera-se que a `Person` lista tenha dois objetos.</span><span class="sxs-lookup"><span data-stu-id="04adc-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="04adc-117">A operação retorna `Person` uma lista de `friends` objetos `Person` que estão nas listas de ambos os objetos na lista de entradas.</span><span class="sxs-lookup"><span data-stu-id="04adc-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
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
  
## <a name="client"></a><span data-ttu-id="04adc-118">Cliente</span><span class="sxs-lookup"><span data-stu-id="04adc-118">Client</span></span>  
 <span data-ttu-id="04adc-119">O proxy do cliente é criado usando o recurso **Add Service Reference** do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="04adc-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="04adc-120">Uma rede social composta `Person` por cinco objetos é criada.</span><span class="sxs-lookup"><span data-stu-id="04adc-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="04adc-121">O cliente liga para cada um dos três métodos do serviço.</span><span class="sxs-lookup"><span data-stu-id="04adc-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="04adc-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="04adc-122">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="04adc-123">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04adc-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="04adc-124">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04adc-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="04adc-125">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="04adc-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="04adc-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="04adc-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="04adc-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="04adc-127">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="04adc-128">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="04adc-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="04adc-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="04adc-129">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="04adc-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="04adc-130">See also</span></span>

- <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>
- [<span data-ttu-id="04adc-131">Referências de objeto de interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="04adc-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
