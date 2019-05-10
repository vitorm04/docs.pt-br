---
title: Ativando o fluxo de transações
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 560b03b8e2788c88e6c92c64834bf36c750575ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626939"
---
# <a name="enabling-transaction-flow"></a>Ativando o fluxo de transações
Windows Communication Foundation (WCF) fornece opções altamente flexíveis para controlar o fluxo de transações. Configurações de fluxo de transações de um serviço podem ser expresso usando uma combinação de atributos e a configuração.  
  
## <a name="transaction-flow-settings"></a>Configurações de fluxo de transação  
 As configurações de fluxo de transação são geradas para um ponto de extremidade de serviço como resultado da interseção dos três valores a seguir:  
  
- O <xref:System.ServiceModel.TransactionFlowAttribute> atributo especificado para cada método no contrato de serviço.  
  
- O `TransactionFlow` associando a propriedade na associação específica.  
  
- O `TransactionFlowProtocol` associando a propriedade na associação específica. O `TransactionFlowProtocol` associando a propriedade permite que você escolha entre os dois protocolos de transação diferentes que você pode usar para fluir uma transação. As seções a seguir descrevem brevemente cada uma delas.  
  
### <a name="ws-atomictransaction-protocol"></a>Protocolo WS-AtomicTransaction  
 O protocolo WS-AtomicTransaction (WS-AT) é útil para cenários quando a interoperabilidade com pilhas de protocolo de terceiros é necessária.  
  
### <a name="oletransactions-protocol"></a>Protocolo de OleTransactions  
 O protocolo de OleTransactions é útil para cenários quando a interoperabilidade com pilhas de protocolo de terceiros não é necessária, e o implantador de um serviço sabe com antecedência que o serviço de protocolo WS-AT está desabilitado localmente ou faz a topologia de rede existente Não, prefira o uso de WS-AT.  
  
 A tabela a seguir mostra os diferentes tipos de fluxos de transação que podem ser gerados usando essas várias combinações.  
  
|TransactionFlow<br /><br /> associação|Propriedade de associação TransactionFlow|Protocolo de associação de TransactionFlowProtocol|Tipo de fluxo de transações|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Obrigatório|true|WS-AT|Transação deve ser colocada em fluxo no formato WS-AT interoperável.|  
|Obrigatório|true|OleTransactions|Transação deve ser colocada em fluxo no formato OleTransactions do WCF.|  
|Obrigatório|false|Não aplicável|Não aplicável porque se trata de uma configuração inválida.|  
|Permitido|true|WS-AT|Transação pode ser colocada no formato WS-AT interoperável.|  
|Permitido|true|OleTransactions|Transação pode ser colocada no formato OleTransactions do WCF.|  
|Permitido|false|Qualquer valor|Uma transação não flui.|  
|NotAllowed|Qualquer valor|Qualquer valor|Uma transação não flui.|  
  
 A tabela a seguir resume as resultados de processamento de mensagens.  
  
|mensagem de entrada|Configuração de TransactionFlow|Cabeçalho da transação|Resultado do processamento de mensagem|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Transação corresponde ao formato esperado de protocolo|Permitido ou obrigatório|`MustUnderstand` é igual a `true`.|Processo|  
|Transação não corresponde ao formato esperado de protocolo|Obrigatório|`MustUnderstand` é igual a `false`.|Rejeitado porque uma transação for necessária|  
|Transação não corresponde ao formato esperado de protocolo|Permitido|`MustUnderstand` é igual a `false`.|Rejeitado porque o cabeçalho não é compreendido.|  
|Usando qualquer formato de protocolo de transação|NotAllowed|`MustUnderstand` é igual a `false`.|Rejeitado porque o cabeçalho não é compreendido.|  
|Nenhuma transação|Obrigatório|N/D|Rejeitado porque uma transação for necessária|  
|Nenhuma transação|Permitido|N/D|Processo|  
|Nenhuma transação|NotAllowed|N/D|Processo|  
  
 Embora cada método em um contrato pode ter requisitos de fluxo de transação diferente, a configuração de protocolo de fluxo de transação está no escopo no nível da associação. Isso significa que todos os métodos que compartilham o mesmo ponto de extremidade (e, portanto, a mesma associação) também compartilham a mesma política permitir ou exigir que o fluxo de transações, bem como o mesmo protocolo de transação se aplicável.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Habilitando o fluxo de transação no nível de método  
 Requisitos de fluxo de transação não são sempre os mesmos para todos os métodos em um contrato de serviço. Portanto, o WCF também fornece um mecanismo baseado em atributo para permitir que as preferências de fluxo de transação de cada método sejam expressas. Isso é feito com o <xref:System.ServiceModel.TransactionFlowAttribute> que especifica o nível no qual uma operação de serviço aceita um cabeçalho de transação. Se você quiser habilitar o fluxo de transações, você deve marcar seus métodos de contrato de serviço com esse atributo. Esse atributo usa um dos valores da <xref:System.ServiceModel.TransactionFlowOption> enumeração, em que o valor padrão é <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Se qualquer valor exceto <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> for especificado, o método é necessário para não ser unidirecional. Um desenvolvedor pode usar esse atributo para especificar restrições ou requisitos de fluxo de transação de nível de método em tempo de design.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Habilitando o fluxo de transação no nível do ponto de extremidade  
 Além da configuração de fluxo de transação de nível de método a <xref:System.ServiceModel.TransactionFlowAttribute> atributo fornece, o WCF fornece uma configuração de todo o ponto de extremidade para o fluxo de transações para permitir que os administradores controlem o fluxo de transações em um nível superior.  
  
 Isso é feito com o <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, que permite habilitar ou desabilitar a entrada de fluxo de transações em um ponto de extremidade de associação configurações, bem como para especificar o formato do protocolo de transação desejadas para transações de entrada.  
  
 Se a associação tiver desabilitado o fluxo de transações, mas uma das operações em um contrato de serviço exige uma transação de entrada, uma exceção de validação é lançada na inicialização do serviço.  
  
 A maioria das associações permanentes contêm o WCF fornece o `transactionFlow` e `transactionProtocol` atributos para que você possa configurar a associação específica para aceitar as transações de entrada. Para obter mais informações sobre como definir os elementos de configuração, consulte [ \<associação >](../../../../docs/framework/misc/binding.md).  
  
 Um administrador ou um implantador pode usar o fluxo de transações de nível de ponto de extremidade para configurar restrições ou requisitos de fluxo de transação no momento da implantação usando o arquivo de configuração.  
  
## <a name="security"></a>Segurança  
 Para garantir a integridade e segurança do sistema, você deve proteger as trocas de mensagens quando fluindo transações entre aplicativos. Você não deve fluir ou divulgar detalhes da transação para qualquer aplicativo que não é qualificado para participar na mesma transação.  
  
 Ao gerar clientes do WCF para serviços Web de desconhecida ou não confiáveis com o uso de troca de metadados, chamadas para operações nesses serviços da Web devem suprimir a transação atual se possível. O exemplo a seguir demonstra como fazer isso.  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Além disso, os serviços devem ser configurados para aceitar as transações de entrada somente de clientes que eles tenham se autenticado e autorizado. Transações de entrada só devem ser aceitas se eles forem provenientes de clientes altamente confiáveis.  
  
## <a name="policy-assertions"></a>Declarações de política  
 O WCF usa as declarações de política para controlar o fluxo de transações. Declarações de política podem ser encontradas no documento de política do serviço, que é gerado por contratos de agregação, configuração e atributos. O cliente pode obter o documento de política do serviço usando uma solicitação-resposta do WS-MetadataExchange ou um HTTP GET. Os clientes, em seguida, podem processar o documento de política para determinar quais operações em um contrato de serviço podem oferecer suporte ou exigir o fluxo de transações.  
  
 Declarações de política de fluxo de transações afetam o fluxo de transações, especificando os cabeçalhos SOAP que um cliente deve enviar para um serviço para representar uma transação. Todos os cabeçalhos de transação devem ser marcados com `MustUnderstand` igual a `true`. Qualquer mensagem com um cabeçalho marcado, caso contrário, será rejeitada com uma falha de SOAP.  
  
 Apenas uma declaração de política de relacionadas à transação pode estar presente em uma única operação. Documentos com mais de uma asserção de transação em uma operação de política são considerados inválidos e são rejeitados pelo WCF. Além disso, apenas um protocolo de transação única pode estar presente em cada tipo de porta. Documentos de política com as operações de referenciar mais de um protocolo de transação dentro de um tipo de porta única são considerados inválidos e são rejeitados pelo [ferramenta de utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Documentos de política com declarações de transação presente nas mensagens de saída ou mensagens de entrada unidirecionais também são consideradas inválidas.
