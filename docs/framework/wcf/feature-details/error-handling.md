---
title: Tratamento de erros
ms.date: 03/30/2017
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
ms.openlocfilehash: 548d93e63440e256ddb54c3ca792a49817c9b059
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49372195"
---
# <a name="error-handling"></a>Tratamento de erros
## <a name="error-handling-in-windows-communication-foundation"></a>Tratamento de erro no Windows Communication Foundation  
 Quando um serviço encontra um erro ou exceção inesperada, há várias maneiras de projetar uma solução de tratamento de exceção. Embora não haja nenhum único "correto" ou "prática recomendada" tratamento de erro de solução, há diversos caminhos válidos para um a considerar. Normalmente é recomendável que um implementar uma solução híbrida que combina várias abordagens da lista abaixo, dependendo da complexidade da implementação do WCF, o tipo e a frequência das exceções, o manipulado versus a natureza sem tratamento das exceções e qualquer rastreamento associado, registro em log ou requisitos de política.  
  
 Essas soluções são explicadas mais profundamente no restante desta seção.  
  
### <a name="the-microsoft-enterprise-library"></a>O Microsoft Enterprise Library  
 O Microsoft Enterprise Library Exception Handling Application Block ajuda a implementar padrões comuns de design e criar uma estratégia consistente de processamento de exceções que ocorrem em todas as camadas de arquiteturas de um aplicativo empresarial. Ele é projetado para dar suporte o código típico contido em instruções catch em componentes do aplicativo. Em vez de repetir esse código (como código que registra as informações de exceção) em blocos catch idêntico ao longo de um aplicativo, o Exception Handling Application Block permite aos desenvolvedores encapsular essa lógica como manipuladores de exceção reutilizáveis.  
  
 Esta biblioteca inclui out-of-the-box um manipulador de exceção de contrato de falha. Este manipulador de exceção foi projetado para uso em limites de serviço do Windows® Communication Foundation (WCF) e gera um novo contrato de falha da exceção.  
  
 Blocos de aplicativos têm como objetivo incorporar práticas recomendadas usadas e fornecer uma abordagem comum para em todo o aplicativo de tratamento de exceções. Por outro lado, os manipuladores de erro personalizada e contratos de falha desenvolvidos por conta própria também podem ser muito útil. Por exemplo, manipuladores de erro personalizadas fornecem uma excelente oportunidade para promover automaticamente todas as exceções para FaultExceptions e também para adicionar recursos de registro em log para seu aplicativo.  
  
 Para obter mais informações, consulte [Microsoft Enterprise Library](https://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Lidando com exceções esperadas  
 O curso apropriado da ação é capturar exceções esperadas em cada operação ou um ponto de extensibilidade relevantes, decidir se pode ser recuperadas e retornar a falha personalizada apropriada em uma FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Lidando com exceções inesperadas usando um IErrorHandler  
 Para lidar com exceções inesperadas, o curso de ação recomendado é "vincular" um IErrorHandler. Manipuladores de erro somente capturam exceções no nível de tempo de execução do WCF (a camada de "modelo de serviço"), não na camada do canal. A única maneira de conectar um IErrorHandler no nível do canal é criar um canal personalizado, que não é recomendado na maioria dos cenários.  
  
 "Exceção inesperada" geralmente não é uma exceção irrecuperável nem uma exceção de processamento; ele é, em vez disso, uma exceção inesperada do usuário. Uma exceção irrecuperável (por exemplo, uma exceção de memória insuficiente) – um geralmente tratada pelos [manipulador de exceção do modelo de serviço](xref:System.ServiceModel.Dispatcher.ExceptionHandler) automaticamente — não podem geralmente ser manipuladas com elegância e o único motivo para tratar essa exceção em todos os pode ser um log adicional ou para retornar uma exceção padrão para o cliente. Uma exceção de processamento ocorre no processamento da mensagem – por exemplo, no codificador, serialização ou nível de formatador – geralmente não podem ser tratadas em um IErrorHandler, porque ele é geralmente muito no início ou muito tarde para o manipulador de erro intervir por a hora em que essas exceções ocorrem. Da mesma forma, as exceções de transporte não podem ser manipuladas em um IErrorHandler.  
  
 Com um IErrorHandler, você pode controlar explicitamente o comportamento do seu aplicativo quando uma exceção é lançada. Você pode:  
  
1.  Decida se deseja ou não enviar uma falha para o cliente  
  
2.  Substituir uma exceção com uma falha  
  
3.  Substituir uma falha por outra falha  
  
4.  Executar o registro em log ou rastreamento  
  
5.  Realizar outras atividades personalizadas  
  
 Um pode instalar um manipulador de erro personalizada ao adicioná-lo à propriedade ErrorHandlers dos dispatchers de canal para o seu serviço.  É possível ter mais de um manipulador de erro e eles são chamados na ordem em que eles são adicionados a esta coleção.  
  
 IErrorHandler.ProvideFault controla a mensagem de falha é enviada ao cliente. Esse método é chamado, independentemente do tipo da exceção gerada por uma operação em seu serviço. Se nenhuma operação é executada aqui, o WCF pressupõe que seu comportamento padrão e continua como se não houvesse nenhum manipulador de erro personalizada no lugar.  
  
 Uma área que você talvez pode usar essa abordagem é quando você deseja criar um local central para converter exceções para falhas antes de serem enviados ao cliente (garantindo que a instância não é descartada e o canal não é movido para o estado de falha).  
  
 O método IErrorHandler.HandleError geralmente é usado para implementar o erro comportamentos relacionados como erro de registro em log, notificações do sistema, desligar o aplicativo, etc. IErrorHandler.HandleError pode ser chamado em vários lugares dentro do serviço e, dependendo de onde o erro é gerado, o método HandleError pode ou não pode ser chamado pelo mesmo thread que a operação. Não há garantias em relação a isso.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Tratamento de exceções fora do WCF  
 Geralmente, exceções de configuração, exceções de cadeia de caracteres de conexão de banco de dados e outras exceções semelhantes podem ocorrer dentro do contexto de um aplicativo WCF, mas são em si não são exceções causadas por modelo de serviço ou o próprio serviço web. Essas exceções são exceções "normais" para o serviço web externas e devem ser manipuladas, assim como outras exceções externas no ambiente devem ser manipuladas.  
  
### <a name="tracing-exceptions"></a>Exceções de rastreamento  
 O rastreamento é o lugar de apenas "capturar tudo", onde é possível ver todas as exceções potencialmente. Para obter mais informações sobre exceções de registro em log e rastreamento, consulte rastreamento e registro em log.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Erros de modelo URI ao usar o WebGetAttribute e WebInvokeAttribute  
 Os atributos WebGet e WebInvoke permitem que você especifique um modelo de URI que mapeia os componentes do endereço da solicitação para os parâmetros da operação. Por exemplo, o modelo de URI "clima / {state} / {cidade}" mapeia o endereço de solicitação em tokens literais, um parâmetro chamado estado e um parâmetro chamado cidade. Esses parâmetros, em seguida, podem ser associados por nome a alguns dos parâmetros formais da operação.  
  
 Os parâmetros de modelo são exibidos na forma de cadeias de caracteres no URI ao parâmetros formais de um contrato com tipo podem ser de tipos de cadeia de caracteres não. Portanto, uma conversão precisa ser feita antes que a operação pode ser invocada. Um [tabela de conversão formatos](wcf-web-http-programming-model-overview.md) está disponível.  
  
 No entanto, se a conversão falhar, então não é possível informar a operação que algo deu errado. Em vez disso, a conversão de tipo revela na forma de uma falha de expedição.  
  
 Uma falha de expedição de conversão de tipo pode ser inspecionado o mesmo assim como acontece com muitos outros tipos de falhas de expedição instalando um manipulador de erro. O ponto de extensibilidade IErrorHandler é chamado para manipular exceções de nível de serviço. A partir daí, a resposta seja enviada para o chamador –, bem como executar quaisquer tarefas personalizadas e emissão de relatórios – pode ser escolhida.  
  
## <a name="see-also"></a>Consulte também  
 [Programação básica do WCF](../basic-wcf-programming.md)
