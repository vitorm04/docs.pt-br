---
title: Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 481d9d7f30f9c2137ec91a87c9743dcb0a97baf7
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816793"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
Este exemplo demonstra como o uso de <xref:System.Runtime.Serialization.DataContractSerializer> com um número apropriado <xref:System.Runtime.Serialization.DataContractResolver> fornece a mesma funcionalidade que <xref:System.Runtime.Serialization.NetDataContractSerializer>. Este exemplo mostra como criar apropriado <xref:System.Runtime.Serialization.DataContractResolver> e como adicioná-lo para o <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Detalhes de exemplo
 <xref:System.Runtime.Serialization.NetDataContractSerializer> difere <xref:System.Runtime.Serialization.DataContractSerializer> de uma maneira importante: <xref:System.Runtime.Serialization.NetDataContractSerializer> inclui informações de tipo CLR em XML serializado, considerando que <xref:System.Runtime.Serialization.DataContractSerializer> não faz isso. Portanto, <xref:System.Runtime.Serialization.NetDataContractSerializer> pode ser usado somente se tanto a serialização e desserialização de extremidades compartilham os mesmos tipos CLR. No entanto, é recomendável usar <xref:System.Runtime.Serialization.DataContractSerializer> porque seu desempenho é melhor do que <xref:System.Runtime.Serialization.NetDataContractSerializer>. Você pode alterar as informações que são serializadas <xref:System.Runtime.Serialization.DataContractSerializer> adicionando um <xref:System.Runtime.Serialization.DataContractResolver> a ele.

 Esse exemplo consiste em dois projetos. O primeiro projeto usa <xref:System.Runtime.Serialization.NetDataContractSerializer> para serializar um objeto. O segundo projeto utiliza <xref:System.Runtime.Serialization.DataContractSerializer> com um <xref:System.Runtime.Serialization.DataContractResolver> para fornecer a mesma funcionalidade que o primeiro projeto.

 O exemplo de código a seguir mostra a implementação de um personalizado <xref:System.Runtime.Serialization.DataContractResolver> nomeado `MyDataContractResolver` que é adicionado para o <xref:System.Runtime.Serialization.DataContractSerializer> no projeto DCSwithDCR.

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

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1.  Usando o Visual Studio 2012, abra o arquivo de solução DCRSample.sln.

2.  O arquivo de solução com o botão direito e escolha **propriedades**.

3.  No **páginas de propriedade da solução** caixa de diálogo, em **propriedades comuns**, **projeto de inicialização**, selecione **vários projetos de inicialização:**.

4.  Ao lado de **DCSwithDCR** projeto, selecione **iniciar** do **ação** lista suspensa.

5.  Ao lado de **NetDCS** projeto, selecione **iniciar** do **ação** lista suspensa.

6.  Clique em **Okey** para fechar a caixa de diálogo.

7.  Para criar a solução, pressione CTRL+SHIFT+B.

8.  Para executar a solução, pressione CTRL+F5.

> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
  
