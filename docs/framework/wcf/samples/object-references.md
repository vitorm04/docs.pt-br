---
title: Referências de objeto
ms.date: 03/30/2017
ms.assetid: 7a93d260-91c3-4448-8f7a-a66fb562fc23
ms.openlocfilehash: 366030cfcbdaa633a1c2f5eb3c9d80bdd7d31ae3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="object-references"></a><span data-ttu-id="e708c-102">Referências de objeto</span><span class="sxs-lookup"><span data-stu-id="e708c-102">Object References</span></span>
<span data-ttu-id="e708c-103">Este exemplo demonstra como passar objetos por referências entre servidor e cliente.</span><span class="sxs-lookup"><span data-stu-id="e708c-103">This sample demonstrates how to pass objects by references between server and client.</span></span> <span data-ttu-id="e708c-104">Exemplos de uso simulados *redes sociais*.</span><span class="sxs-lookup"><span data-stu-id="e708c-104">The sample uses simulated *social networks*.</span></span> <span data-ttu-id="e708c-105">Consiste em uma rede social um `Person` que contém uma lista de amigos no qual cada friend é uma instância da classe de `Person` classe, com sua própria lista de amigos.</span><span class="sxs-lookup"><span data-stu-id="e708c-105">A social network consists of a `Person` class that contains a list of friends in which each friend is an instance of the `Person` class, with its own list of friends.</span></span> <span data-ttu-id="e708c-106">Isso cria um gráfico de objetos.</span><span class="sxs-lookup"><span data-stu-id="e708c-106">This creates a graph of objects.</span></span> <span data-ttu-id="e708c-107">O serviço expõe operações nessas redes sociais.</span><span class="sxs-lookup"><span data-stu-id="e708c-107">The service exposes operations on these social networks.</span></span>  
  
 <span data-ttu-id="e708c-108">Neste exemplo, o serviço é hospedado por serviços de informações da Internet (IIS) e o cliente é um aplicativo de console (.exe).</span><span class="sxs-lookup"><span data-stu-id="e708c-108">In this sample, the service is hosted by Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e708c-109">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="e708c-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="service"></a><span data-ttu-id="e708c-110">Serviço</span><span class="sxs-lookup"><span data-stu-id="e708c-110">Service</span></span>  
 <span data-ttu-id="e708c-111">O `Person` classe tem o <xref:System.Runtime.Serialization.DataContractAttribute> atributo aplicado, com o <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> campo definido como `true` para declará-la como um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="e708c-111">The `Person` class has the <xref:System.Runtime.Serialization.DataContractAttribute> attribute applied, with the <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A> field set to `true` to declare it as a reference type.</span></span> <span data-ttu-id="e708c-112">Todas as propriedades têm o <xref:System.Runtime.Serialization.DataMemberAttribute> atributo aplicado.</span><span class="sxs-lookup"><span data-stu-id="e708c-112">All properties have the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute applied.</span></span>  
  
```  
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
  
 <span data-ttu-id="e708c-113">O `GetPeopleInNetwork` operação aceita um parâmetro de tipo `Person` e retorna todas as pessoas na rede; ou seja, todas as pessoas a `friends` lista o amigo amigos e assim por diante, sem duplicatas.</span><span class="sxs-lookup"><span data-stu-id="e708c-113">The `GetPeopleInNetwork` operation takes a parameter of type `Person` and returns all the people in the network; that is, all the people in the `friends` list, the friend's friends, and so on, without duplicates.</span></span>  
  
```  
public List<Person> GetPeopleInNetwork(Person p)  
{  
    List<Person> people = new List<Person>();  
    ListPeopleInNetwork(p, people);  
    return people;  
  
}  
```  
  
 <span data-ttu-id="e708c-114">O `GetMutualFriends` operação aceita um parâmetro de tipo `Person` e retorna todos os amigos na lista que também têm essa pessoa em seus `friends` lista.</span><span class="sxs-lookup"><span data-stu-id="e708c-114">The `GetMutualFriends` operation takes a parameter of type `Person` and returns all the friends in the list who also have this person in their `friends` list.</span></span>  
  
```  
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
  
 <span data-ttu-id="e708c-115">O `GetCommonFriends` operação usa uma lista do tipo `Person`.</span><span class="sxs-lookup"><span data-stu-id="e708c-115">The `GetCommonFriends` operation takes a list of type `Person`.</span></span> <span data-ttu-id="e708c-116">A lista deve ter dois `Person` objetos contidos nele.</span><span class="sxs-lookup"><span data-stu-id="e708c-116">The list is expected to have two `Person` objects in it.</span></span> <span data-ttu-id="e708c-117">A operação retorna uma lista de `Person` objetos que estão na `friends` listas de ambos `Person` objetos na lista de entrada.</span><span class="sxs-lookup"><span data-stu-id="e708c-117">The operation returns a list of `Person` objects that are in the `friends` lists of both `Person` objects in the input list.</span></span>  
  
```  
public List<Person> GetCommonFriends(List<Person> people)  
{  
    List<Person> common = new List<Person>();  
    foreach (Person friend in people[0].Friends)  
        if (people[1].Friends.Contains(friend))  
            common.Add(friend);  
    return common;  
}  
```  
  
## <a name="client"></a><span data-ttu-id="e708c-118">Cliente</span><span class="sxs-lookup"><span data-stu-id="e708c-118">Client</span></span>  
 <span data-ttu-id="e708c-119">O proxy do cliente é criado usando o **adicionar referência de serviço** recurso do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e708c-119">The client proxy is created using the **Add Service Reference** feature of Visual Studio.</span></span>  
  
 <span data-ttu-id="e708c-120">Uma rede social que consiste em cinco `Person` objetos é criado.</span><span class="sxs-lookup"><span data-stu-id="e708c-120">A social network that consists of five `Person` objects is created.</span></span> <span data-ttu-id="e708c-121">O cliente chama cada um dos três métodos no serviço.</span><span class="sxs-lookup"><span data-stu-id="e708c-121">The client calls each of the three methods in the service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e708c-122">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="e708c-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="e708c-123">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e708c-123">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="e708c-124">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e708c-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="e708c-125">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e708c-125">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e708c-126">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="e708c-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e708c-127">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="e708c-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e708c-128">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="e708c-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e708c-129">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="e708c-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\ObjectReferences`  
  
## <a name="see-also"></a><span data-ttu-id="e708c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e708c-130">See Also</span></span>  
 <xref:System.Runtime.Serialization.DataContractAttribute.IsReference%2A>  
 [<span data-ttu-id="e708c-131">Referências de objeto interoperável</span><span class="sxs-lookup"><span data-stu-id="e708c-131">Interoperable Object References</span></span>](../../../../docs/framework/wcf/feature-details/interoperable-object-references.md)
