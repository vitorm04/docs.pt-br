---
title: Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: d7102e60c8b5302d4f3bc83b356dbc7de117f57a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039870"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="f2c0e-102">Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer</span><span class="sxs-lookup"><span data-stu-id="f2c0e-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>
<span data-ttu-id="f2c0e-103">Este exemplo demonstra como o uso do <xref:System.Runtime.Serialization.DataContractSerializer> com um apropriado <xref:System.Runtime.Serialization.DataContractResolver> fornece a mesma funcionalidade que <xref:System.Runtime.Serialization.NetDataContractSerializer>o.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f2c0e-104">Este exemplo mostra como criar o apropriado <xref:System.Runtime.Serialization.DataContractResolver> e como adicioná-lo <xref:System.Runtime.Serialization.DataContractSerializer>ao.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="f2c0e-105">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="f2c0e-105">Sample details</span></span>
 <span data-ttu-id="f2c0e-106"><xref:System.Runtime.Serialization.NetDataContractSerializer>difere de <xref:System.Runtime.Serialization.DataContractSerializer> uma maneira importante: <xref:System.Runtime.Serialization.NetDataContractSerializer> inclui informações de tipo CLR no XML serializado, enquanto <xref:System.Runtime.Serialization.DataContractSerializer> não faz isso.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="f2c0e-107">Portanto, <xref:System.Runtime.Serialization.NetDataContractSerializer> pode ser usado somente se a serialização e a desserialização terminarem de compartilhar os mesmos tipos CLR.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="f2c0e-108">No entanto, é recomendável <xref:System.Runtime.Serialization.DataContractSerializer> usar porque seu desempenho é melhor <xref:System.Runtime.Serialization.NetDataContractSerializer>do que.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="f2c0e-109">Você pode alterar as informações que são serializadas <xref:System.Runtime.Serialization.DataContractSerializer> no adicionando uma <xref:System.Runtime.Serialization.DataContractResolver> a ela.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="f2c0e-110">Este exemplo consiste em dois projetos.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-110">This sample consists of two projects.</span></span> <span data-ttu-id="f2c0e-111">O primeiro projeto usa <xref:System.Runtime.Serialization.NetDataContractSerializer> para serializar um objeto.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="f2c0e-112">O segundo projeto usa <xref:System.Runtime.Serialization.DataContractSerializer> com um <xref:System.Runtime.Serialization.DataContractResolver> para fornecer a mesma funcionalidade que o primeiro projeto.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="f2c0e-113">O exemplo de código a seguir mostra a implementação de <xref:System.Runtime.Serialization.DataContractResolver> um `MyDataContractResolver` nome personalizado <xref:System.Runtime.Serialization.DataContractSerializer> que é adicionado ao no projeto DCSwithDCR.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        if (type == null)
        {
            type = Type.GetType(typeName + ", " + typeNamespace);
        }
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="f2c0e-114">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="f2c0e-114">To use this sample</span></span>

1. <span data-ttu-id="f2c0e-115">Usando o Visual Studio 2012, abra o arquivo de solução DCRSample. sln.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="f2c0e-116">Clique com o botão direito do mouse no arquivo de solução e escolha **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="f2c0e-117">Na caixa de diálogo **páginas de propriedades da solução** , em **Propriedades comuns**, **projeto de inicialização**, selecione **vários projetos de inicialização:** .</span><span class="sxs-lookup"><span data-stu-id="f2c0e-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="f2c0e-118">Ao lado do projeto **DCSwithDCR** , selecione **Iniciar** na lista suspensa **ação** .</span><span class="sxs-lookup"><span data-stu-id="f2c0e-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="f2c0e-119">Ao lado do projeto **NetDCS** , selecione **Iniciar** na lista suspensa **ação** .</span><span class="sxs-lookup"><span data-stu-id="f2c0e-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="f2c0e-120">Clique em **OK** para fechar a caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="f2c0e-121">Para criar a solução, pressione CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="f2c0e-122">Para executar a solução, pressione CTRL+F5.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2c0e-123">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f2c0e-124">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-124">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="f2c0e-125">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f2c0e-126">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="f2c0e-126">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
