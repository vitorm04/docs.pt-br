---
title: Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e52b6da80100cbffb7dc8725d16c31a67bc19445
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351657"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
Este exemplo demonstra como o uso de <xref:System.Runtime.Serialization.DataContractSerializer> com um <xref:System.Runtime.Serialization.DataContractResolver> apropriado fornece a mesma funcionalidade que <xref:System.Runtime.Serialization.NetDataContractSerializer>. Este exemplo mostra como criar o <xref:System.Runtime.Serialization.DataContractResolver> apropriado e como adicioná-lo ao <xref:System.Runtime.Serialization.DataContractSerializer>.

## <a name="sample-details"></a>Detalhes de exemplo
 <xref:System.Runtime.Serialization.NetDataContractSerializer> difere de <xref:System.Runtime.Serialization.DataContractSerializer> de uma maneira importante: <xref:System.Runtime.Serialization.NetDataContractSerializer> inclui informações de tipo CLR no XML serializado, enquanto <xref:System.Runtime.Serialization.DataContractSerializer> não. Portanto, <xref:System.Runtime.Serialization.NetDataContractSerializer> só poderá ser usado se a serialização e desserialização terminarem os mesmos tipos CLR. No entanto, é recomendável usar <xref:System.Runtime.Serialization.DataContractSerializer> porque seu desempenho é melhor do que <xref:System.Runtime.Serialization.NetDataContractSerializer>. Você pode alterar as informações serializadas no <xref:System.Runtime.Serialization.DataContractSerializer> adicionando um <xref:System.Runtime.Serialization.DataContractResolver> a ela.

 Este exemplo consiste em dois projetos. O primeiro projeto usa <xref:System.Runtime.Serialization.NetDataContractSerializer> para serializar um objeto. O segundo projeto usa <xref:System.Runtime.Serialization.DataContractSerializer> com um <xref:System.Runtime.Serialization.DataContractResolver> para fornecer a mesma funcionalidade que o primeiro projeto.

 O exemplo de código a seguir mostra a implementação de um <xref:System.Runtime.Serialization.DataContractResolver> personalizado chamado `MyDataContractResolver` que é adicionado ao <xref:System.Runtime.Serialization.DataContractSerializer> no projeto DCSwithDCR.

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
        type ??= Type.GetType(typeName + ", " + typeNamespace);
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

1. Usando o Visual Studio 2012, abra o arquivo de solução DCRSample. sln.

2. Clique com o botão direito do mouse no arquivo de solução e escolha **Propriedades**.

3. Na caixa de diálogo **páginas de propriedades da solução** , em **Propriedades comuns**, **projeto de inicialização**, selecione **vários projetos de inicialização:** .

4. Ao lado do projeto **DCSwithDCR** , selecione **Iniciar** na lista suspensa **ação** .

5. Ao lado do projeto **NetDCS** , selecione **Iniciar** na lista suspensa **ação** .

6. Clique em **OK** para fechar a caixa de diálogo.

7. Para criar a solução, pressione CTRL+SHIFT+B.

8. Para executar a solução, pressione CTRL+F5.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) [!INCLUDE[wf1](../../../../includes/wf1-md.md)] e exemplos. Este exemplo está localizado no seguinte diretório.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
