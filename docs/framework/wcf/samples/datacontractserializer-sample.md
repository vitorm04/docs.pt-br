---
title: Exemplo de DataContractSerializer
ms.date: 03/30/2017
helpviewer_keywords:
- XML Formatter
ms.assetid: e0a2fe89-3534-48c8-aa3c-819862224571
ms.openlocfilehash: 0086bdd41b9f87c14b3a9d0653a8f8982235b1ad
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188593"
---
# <a name="datacontractserializer-sample"></a>Exemplo de DataContractSerializer
O exemplo de DataContractSerializer demonstra o <xref:System.Runtime.Serialization.DataContractSerializer>, que executa a serialização geral e a desserialização de serviços para os dados de classes de contrato. O exemplo cria um `Record` do objeto, serializa-lo para um fluxo de memória e desserializa o fluxo de memória para outro `Record` objeto demonstrar o uso do <xref:System.Runtime.Serialization.DataContractSerializer>. O exemplo, em seguida, serializa o `Record` usando um gravador binário para demonstrar como o gravador afeta a serialização do objeto.  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 O contrato de dados para `Record` é mostrado no código de exemplo a seguir.  
  
```csharp  
[DataContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
internal class Record  
{  
    private double n1;  
    private double n2;  
    private string operation;  
    private double result;  
  
    internal Record(double n1, double n2, string operation, double result)  
    {  
        this.n1 = n1;  
        this.n2 = n2;  
        this.operation = operation;  
        this.result = result;  
    }  
  
    [DataMember]  
    internal double OperandNumberOne  
    {  
        get { return n1; }  
        set { n1 = value; }  
    }  
  
    [DataMember]  
    internal double OperandNumberTwo  
    {  
        get { return n2; }  
        set { n2 = value; }  
    }  
  
    [DataMember]  
    internal string Operation  
    {  
        get { return operation; }  
        set { operation = value; }  
    }  
  
    [DataMember]  
    internal double Result  
    {  
        get { return result; }  
        set { result = value; }  
    }  
  
    public override string ToString()  
    {  
        return string.Format("Record: {0} {1} {2} = {3}", n1,  
            operation, n2, result);  
    }  
}  
```  
  
 O código de exemplo cria um `Record` objeto chamado `record1` , em seguida, exibe o objeto.  
  
```csharp
Record record1 = new Record(1, 2, "+", 3);  
Console.WriteLine("Original record: {0}", record1.ToString());  
```  
  
 O exemplo, em seguida, usa o <xref:System.Runtime.Serialization.DataContractSerializer> para serializar `record1` em um fluxo de memória.  
  
```csharp  
MemoryStream stream1 = new MemoryStream();  
  
//Serialize the Record object to a memory stream using DataContractSerializer.  
DataContractSerializer serializer = new DataContractSerializer(typeof(Record));  
serializer.WriteObject(stream1, record1);  
```  
  
 Em seguida, o exemplo usa o <xref:System.Runtime.Serialization.DataContractSerializer> para desserializar o fluxo de memória em um novo `Record` do objeto e o exibe.  
  
```csharp  
stream1.Position = 0;  
  
//Deserialize the Record object back into a new record object.  
Record record2 = (Record)serializer.ReadObject(stream1);  
  
Console.WriteLine("Deserialized record: {0}", record2.ToString());  
```  
  
 Por padrão, o `DataContractSerializer` codifica os objetos em um fluxo usando uma representação textual do XML. No entanto, você pode influenciar a codificação do XML, passando um gravador diferente. O exemplo cria um gravador binário chamando <xref:System.Xml.XmlDictionaryWriter.CreateBinaryWriter%2A>. Ele passa o gravador e o objeto de registro para o serializador quando ele chama <xref:System.Runtime.Serialization.DataContractSerializer.WriteObjectContent%2A>. Por fim, o exemplo libera o gravador e relatórios sobre o comprimento dos fluxos.  
  
```csharp  
MemoryStream stream2 = new MemoryStream();  
  
XmlDictionaryWriter binaryDictionaryWriter = XmlDictionaryWriter.CreateBinaryWriter(stream2);  
serializer.WriteObject(binaryDictionaryWriter, record1);  
binaryDictionaryWriter.Flush();  
  
//report the length of the streams  
Console.WriteLine("Text Stream is {0} bytes long", stream1.Length);  
Console.WriteLine("Binary Stream is {0} bytes long", stream2.Length);  
```  
  
 Quando você executar o exemplo, o registro original e o registro desserializado são exibidos, seguido por meio da comparação entre o comprimento da codificação de texto e a codificação binária. Pressione ENTER na janela do cliente para desligar o cliente.  
  
```console  
Original record: Record: 1 + 2 = 3  
Deserialized record: Record: 1 + 2 = 3  
Text Stream is 233 bytes long  
Binary Stream is 156 bytes long  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Para executar o exemplo, inicie o cliente do prompt de comando digitando client\bin\client.exe.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\DataContractSerializer`  
  
## <a name="see-also"></a>Consulte também
