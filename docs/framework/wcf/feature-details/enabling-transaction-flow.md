---
title: Ativando o fluxo de transações
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 180fc99195444057c5bbb4a1679e948f9ddf1830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-transaction-flow"></a>Ativando o fluxo de transações
Windows Communication Foundation (WCF) fornece opções altamente flexíveis para controlar o fluxo de transações. Configurações de fluxo de transações do serviço podem ser expressadas usando uma combinação de atributos e configuração.  
  
## <a name="transaction-flow-settings"></a>Configurações de fluxo de transações  
 Configurações de fluxo de transação são geradas para um ponto de extremidade de serviço como resultado da interseção dos três valores a seguir:  
  
-   O <xref:System.ServiceModel.TransactionFlowAttribute> atributo especificado para cada método de contrato de serviço.  
  
-   O `TransactionFlow` a propriedade binding na associação específica.  
  
-   O `TransactionFlowProtocol` a propriedade binding na associação específica. O `TransactionFlowProtocol` a propriedade binding permite que você escolha entre os dois protocolos de transação diferentes que você pode usar para transmitir uma transação. As seções a seguir descrevem brevemente cada um deles.  
  
### <a name="ws-atomictransaction-protocol"></a>Protocolo WS-AtomicTransaction  
 O protocolo WS-AtomicTransaction (WS-AT) é útil para cenários quando a interoperabilidade com pilhas de protocolo de terceiros é necessária.  
  
### <a name="oletransactions-protocol"></a>Protocolo OleTransactions  
 O protocolo OleTransactions é útil para cenários quando interoperabilidade com pilhas de protocolo de terceiros não é necessária, e o implantador de um serviço sabe com antecedência que o serviço de protocolo WS-AT está desabilitado localmente ou não de topologia de rede existente não favorecer o uso de WS-AT.  
  
 A tabela a seguir mostra os diferentes tipos de fluxos de transação que podem ser gerados usando essas várias combinações.  
  
|TransactionFlow<br /><br /> associação|Propriedade de associação TransactionFlow|Protocolo de associação de TransactionFlowProtocol|Tipo de fluxo de transações|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Obrigatório|true|WS-AT|Transação deve ser colocada no formato WS-AT interoperável.|  
|Obrigatório|true|OleTransactions|Transação deve ser colocada no formato OleTransactions WCF.|  
|Obrigatório|false|Não aplicável|Não aplicável porque esta é uma configuração inválida.|  
|Permitido|true|WS-AT|Transação pode ser colocada no formato WS-AT interoperável.|  
|Permitido|true|OleTransactions|Transação pode ser colocada no formato OleTransactions WCF.|  
|Permitido|false|Qualquer valor|Não resulta em uma transação.|  
|Não permitido|Qualquer valor|Qualquer valor|Não resulta em uma transação.|  
  
 A tabela a seguir resume as resultados de processamento de mensagens.  
  
|Mensagem de entrada|Configuração de TransactionFlow|Cabeçalho da transação|Resultado do processamento de mensagem|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Transação coincide com o formato do protocolo esperado|Permitido ou obrigatório|`MustUnderstand` é igual a `true`.|Processo|  
|Transação não coincide com formato do protocolo esperado|Obrigatório|`MustUnderstand` é igual a `false`.|Rejeitado porque uma transação é necessária|  
|Transação não coincide com formato do protocolo esperado|Permitido|`MustUnderstand` é igual a `false`.|Rejeitado porque o cabeçalho não é compreendido.|  
|Usando qualquer formato de protocolo de transação|Não permitido|`MustUnderstand` é igual a `false`.|Rejeitado porque o cabeçalho não é compreendido.|  
|Nenhuma transação|Obrigatório|N/D|Rejeitado porque uma transação é necessária|  
|Nenhuma transação|Permitido|N/D|Processo|  
|Nenhuma transação|Não permitido|N/D|Processo|  
  
 Enquanto cada método em um contrato pode ter requisitos de fluxo de transação diferente, a configuração de protocolo de fluxo de transações tem seu escopo definida no nível de associação. Isso significa que todos os métodos que compartilham o mesmo ponto de extremidade (e, portanto, a mesma associação) também compartilham a mesma política de permissão ou não exigir o fluxo de transação, bem como o mesmo protocolo de transação, se aplicável.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Ativando o fluxo de transação no nível de método  
 Requisitos de fluxo de transação não são sempre o mesmo para todos os métodos em um contrato de serviço. Portanto, o WCF também fornece um mecanismo baseado em atributos para permitir que as preferências de fluxo de transação de cada método sejam expressas. Isso é obtido com o <xref:System.ServiceModel.TransactionFlowAttribute> que especifica o nível no qual uma operação de serviço aceita um cabeçalho de transação. Se você deseja habilitar o fluxo de transações, você deve marcar seus métodos de contrato de serviço com esse atributo. Este atributo tem um dos valores da <xref:System.ServiceModel.TransactionFlowOption> enumeração, em que o valor padrão é <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Se qualquer valor exceto <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> for especificado, o método é necessário para não ser unidirecional. Um desenvolvedor pode usar esse atributo para especificar restrições ou requisitos de fluxo de transação de nível de método em tempo de design.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Ativando o fluxo de transação no nível do ponto de extremidade  
 Além da configuração de fluxo de transação de nível de método de <xref:System.ServiceModel.TransactionFlowAttribute> atributo fornece WCF fornece uma configuração de todo o ponto de extremidade para o fluxo de transações para permitir que os administradores controlar o fluxo de transações em um nível superior.  
  
 Isso é obtido com o <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, que permite habilitar ou desabilitar o fluxo de transações de entrada em um ponto de extremidade do configurações de associação, bem como para especificar o formato do protocolo desejado de transação para transações de entrada.  
  
 Se a associação tiver desabilitado o fluxo de transações, mas uma das operações em um contrato de serviço exige uma transação de entrada, uma exceção de validação é lançada durante a inicialização do serviço.  
  
 A maioria das associações aguardando WCF fornece contêm o `transactionFlow` e `transactionProtocol` atributos para que você possa configurar a associação específica para aceitar as transações de entrada. Para obter mais informações sobre como definir os elementos de configuração, consulte [ \<associação >](../../../../docs/framework/misc/binding.md).  
  
 Um administrador ou implantador pode usar o fluxo de transações de nível de ponto de extremidade para configurar restrições ou requisitos de transação de fluxo no momento da implantação usando o arquivo de configuração.  
  
## <a name="security"></a>Segurança  
 Para garantir a integridade e segurança do sistema, você deve proteger as trocas de mensagens ao fluir transações entre aplicativos. Você não deve fluxo ou divulgar detalhes da transação para qualquer aplicativo que não está qualificada para participar na mesma transação.  
  
 Ao gerar os clientes WCF desconhecidos ou não confiáveis serviços Web com o uso de troca de metadados, chamadas para operações nesses serviços da Web devem suprimir a transação atual se possível. O exemplo a seguir demonstra como fazer isso.  
  
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
  
 Além disso, os serviços devem ser configurados para aceitar as transações de entrada somente de clientes que eles têm autenticado e autorizado. Transações de entrada devem ser aceita somente se eles forem provenientes de clientes altamente confiáveis.  
  
## <a name="policy-assertions"></a>Declarações de política  
 WCF usa declarações de política para controlar o fluxo de transações. Declarações de política podem ser encontradas no documento de política do serviço, que é gerado por contratos de agregação, configuração e atributos. O cliente pode obter o documento de política do serviço usando um HTTP GET ou uma resposta de solicitação do WS-MetadataExchange. Os clientes podem processar o documento de política para determinar quais operações em um contrato de serviço podem dar suporte a ou exigir o fluxo de transações.  
  
 Declarações de política de fluxo de transações afetam o fluxo de transações, especificando os cabeçalhos SOAP que um cliente deve enviar para um serviço para representar uma transação. Todos os cabeçalhos de transação devem ser marcados com `MustUnderstand` igual a `true`. Qualquer mensagem com um cabeçalho marcada caso contrário é rejeitada com uma falha de SOAP.  
  
 Somente uma declaração de política relacionadas à transação pode estar presente em uma única operação. Documentos de política com mais de uma declaração de transação em uma operação são considerados inválidos e serão rejeitados pelo WCF. Além disso, um protocolo de transação única pode estar presente em cada tipo de porta. Documentos de política com operações fazendo referência a mais de um protocolo de transação dentro de um único tipo de porta são considerados inválidos e serão rejeitados pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Documentos de política com declarações de transação presente nas mensagens de saída ou mensagens de entrada unidirecionais também são consideradas inválidas.
