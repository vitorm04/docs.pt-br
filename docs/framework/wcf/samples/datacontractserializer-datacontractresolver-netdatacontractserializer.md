---
title: Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: e7a4f0d754b444d8558b03e07d98788a2eee5971
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144976"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a>Uso de DataContractSerializer e de DataContractResolver para fornecer a funcionalidade NetDataContractSerializer
Esta amostra demonstra como <xref:System.Runtime.Serialization.DataContractSerializer> o <xref:System.Runtime.Serialization.DataContractResolver> uso de um <xref:System.Runtime.Serialization.NetDataContractSerializer>apropriado fornece a mesma funcionalidade que . Esta amostra mostra como <xref:System.Runtime.Serialization.DataContractResolver> criar o apropriado e <xref:System.Runtime.Serialization.DataContractSerializer>como adicioná-lo ao .

## <a name="sample-details"></a>Detalhes de exemplo
 <xref:System.Runtime.Serialization.NetDataContractSerializer>difere de <xref:System.Runtime.Serialization.DataContractSerializer> uma forma <xref:System.Runtime.Serialization.NetDataContractSerializer> importante: inclui informações do tipo CLR no <xref:System.Runtime.Serialization.DataContractSerializer> XML serializado, enquanto não. Portanto, <xref:System.Runtime.Serialization.NetDataContractSerializer> só pode ser usado se as extremidades serializadora e desserializadora compartilharem os mesmos tipos de CLR. No entanto, recomenda-se usar <xref:System.Runtime.Serialization.DataContractSerializer> porque <xref:System.Runtime.Serialization.NetDataContractSerializer>seu desempenho é melhor do que . Você pode alterar as informações <xref:System.Runtime.Serialization.DataContractSerializer> que são <xref:System.Runtime.Serialization.DataContractResolver> serializadas adicionando a ela.

 Esta amostra consiste em dois projetos. O primeiro <xref:System.Runtime.Serialization.NetDataContractSerializer> projeto usa para serializar um objeto. O segundo <xref:System.Runtime.Serialization.DataContractSerializer> projeto <xref:System.Runtime.Serialization.DataContractResolver> usa com a para fornecer a mesma funcionalidade do primeiro projeto.

 O exemplo de código a <xref:System.Runtime.Serialization.DataContractResolver> seguir `MyDataContractResolver` mostra a <xref:System.Runtime.Serialization.DataContractSerializer> implementação de um personalizado nomeado que é adicionado ao projeto DCSwithDCR.

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

1. Usando o Visual Studio 2012, abra o arquivo de solução DCRSample.sLn.

2. Clique com o botão direito do mouse no arquivo da solução e escolha **Propriedades**.

3. Na caixa de diálogo Páginas de propriedade de **solução,** em **Propriedades Comuns,** **Projeto de Inicialização,** selecione **Vários projetos de inicialização:**.

4. Ao lado do projeto **DCSwithDCR,** **selecione Iniciar** a partir da parada **Ação.**

5. Ao lado do projeto **NetDCS,** **selecione Iniciar** a partir da parada **Ação.**

6. Clique em **OK** para fechar o diálogo.

7. Para criar a solução, pressione CTRL+SHIFT+B.

8. Para executar a solução, pressione CTRL+F5.

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
