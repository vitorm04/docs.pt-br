---
title: Cabeçalhos de endereço
ms.date: 03/30/2017
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
ms.openlocfilehash: 4ccb309178251b32068d6cdbb81874322f991bb9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002944"
---
# <a name="address-headers"></a>Cabeçalhos de endereço

O exemplo de cabeçalhos de endereço demonstra como os clientes podem passar parâmetros de referência a um serviço usando o Windows Communication Foundation (WCF).

> [!NOTE]
> As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.

A especificação de WS-Addressing define a noção de uma referência de ponto de extremidade como uma maneira de resolver um ponto de extremidade de serviço Web específico. No WCF, referências de ponto de extremidade são modeladas usando o `EndpointAddress` classe - `EndpointAddress` é o tipo de campo de endereço do `ServiceEndpoint` classe.

Parte do modelo de referência de ponto de extremidade é que cada referência pode executar alguns parâmetros de referência que adicionar informações de identificação extra. No WCF, esses parâmetros de referência são modelados como instâncias de `AddressHeader` classe.

Neste exemplo, o cliente adiciona um parâmetro de referência para o `EndpointAddress` do ponto de extremidade de cliente. O serviço procura esse parâmetro de referência e use seu valor na lógica de sua operação de serviço "Hello".

## <a name="client"></a>Cliente

Para o cliente enviar um parâmetro de referência, ele deve adicionar um `AddressHeader` para o `EndpointAddress` da `ServiceEndpoint`. Porque o `EndpointAddress` classe é imutável, a modificação de um endereço de ponto de extremidade deve ser feita usando o `EndpointAddressBuilder` classe. O código a seguir inicializa o cliente para enviar um parâmetro de referência como parte de sua mensagem.

```csharp
HelloClient client = new HelloClient();
EndpointAddressBuilder builder =
    new EndpointAddressBuilder(client.Endpoint.Address);
AddressHeader header =
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");
builder.Headers.Add(header);
client.Endpoint.Address = builder.ToEndpointAddress();
```

O código cria um `EndpointAddressBuilder` usando o original `EndpointAddress` como um valor inicial. Depois, ele adiciona um cabeçalho de endereço recém-criado. a chamada para `CreateAddressHeader` cria um cabeçalho com um determinado nome, namespace e valor. Aqui, o valor é "John". Depois que o cabeçalho é adicionado ao construtor, o `ToEndpointAddress()` método converte o construtor (mutável) volta para um endereço de ponto de extremidade (imutáveis), que é atribuído de volta ao campo de endereço do ponto de extremidade de cliente.

Agora quando o cliente chama `Console.WriteLine(client.Hello());`, o serviço é capaz de obter o valor desse parâmetro de endereço, como mostra a saída resultante do cliente.

`Hello, John`

## <a name="server"></a>Servidor

A implementação da operação de serviço `Hello()` usa atual `OperationContext` para inspecionar os valores dos cabeçalhos na mensagem de entrada.

```csharp
string id = null;
// look at headers on incoming message
for (int i = 0;
     i < OperationContext.Current.IncomingMessageHeaders.Count;
     ++i)
{
    MessageHeaderInfo h = OperationContext.Current.IncomingMessageHeaders[i];
    // for any reference parameters with the correct name & namespace
    if (h.IsReferenceParameter &&
        h.Name == IDName &&
        h.Namespace == IDNamespace)
    {
        // read the value of that header
        XmlReader xr = OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);
        id = xr.ReadElementContentAsString();
    }
}
return "Hello, " + id;
```

O código itera em todos os cabeçalhos na mensagem de entrada, procurando os cabeçalhos que são parâmetros de referência com o nome específico e. Quando o parâmetro for encontrado, ele lê o valor do parâmetro e o armazena na variável "id".

#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo

1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).

2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).

3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).

> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`
