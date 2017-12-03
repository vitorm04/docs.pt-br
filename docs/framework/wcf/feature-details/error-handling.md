---
title: Tratamento de erros
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c948841a-7db9-40ae-9b78-587d216cbcaf
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 215fb30772e4f1b25e20303b3f83d6fe0c00ebae
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="error-handling"></a>Tratamento de erros
## <a name="error-handling-in-windows-communication-foundation"></a>Tratamento de erro no Windows Communication Foundation  
 Quando um serviço encontra um erro ou exceção inesperada, há várias maneiras de desenvolver uma solução de tratamento de exceção. Embora não haja nenhum único "correto" ou "prática recomendada" tratamento de erros solução, há diversos caminhos válidos para um considerar. Normalmente é recomendável que um implementar uma solução híbrida que combina várias abordagens da lista abaixo, dependendo da complexidade da implementação de WCF, o tipo e a frequência das exceções, o manipulada versus natureza sem tratamento das exceções e qualquer associada rastreamento, log ou requisitos de política.  
  
 Essas soluções são explicadas mais profundamente no restante desta seção.  
  
### <a name="the-microsoft-enterprise-library"></a>O Microsoft Enterprise Library  
 O Microsoft Enterprise Library Exception Handling Application Block ajuda a implementar os padrões comuns de design e criar uma estratégia consistente de processamento de exceções que ocorrem em todas as camadas de arquitetura de um aplicativo corporativo. Ele foi projetado para dar suporte o código típico contido em instruções de captura em componentes do aplicativo. Em vez de repetir este código (por exemplo, o código que registra informações de exceção) em blocos catch idêntico em um aplicativo, o bloco de aplicativo de tratamento de exceção permite aos desenvolvedores encapsular essa lógica como manipuladores de exceção reutilizáveis.  
  
 Essa biblioteca inclui de-prontos um manipulador de exceção de contrato de falha. Este manipulador de exceção é projetado para uso em limites de serviço do Windows® Communication Foundation (WCF) e gera um novo contrato de falha da exceção.  
  
 Blocos de aplicativos visam incorporam práticas recomendadas usadas e fornecer uma abordagem comum para seu aplicativo de tratamento de exceção. Por outro lado, manipuladores de erro personalizada e contratos de falha desenvolvidos por conta própria também podem ser muito útil. Por exemplo, manipuladores de erro personalizado fornecem uma excelente oportunidade para promover automaticamente todas as exceções a FaultExceptions e também para adicionar recursos de registro ao seu aplicativo.  
  
 Para obter mais informações, consulte [Microsoft Enterprise Library](http://msdn.microsoft.com/library/ff632023.aspx).  
  
### <a name="dealing-with-expected-exceptions"></a>Lidando com exceções esperadas  
 O adequada da ação é capturar exceções esperadas em cada operação ou um ponto de extensibilidade relevantes, decida se pode ser recuperados do e retornar a falha personalizada apropriada em uma FaultException\<T >  
  
### <a name="dealing-with-unexpected-exceptions-using-an-ierrorhandler"></a>Lidando com exceções inesperadas, usando um IErrorHandler  
 Para lidar com exceções inesperadas, o curso de ação recomendado é um IErrorHandler "conectar". Manipuladores de erro capturam somente exceções no nível de tempo de execução do WCF (a camada de "modelo de serviço"), não na camada do canal. É a única maneira de conectar um IErrorHandler no nível do canal criar um canal personalizado, que não é recomendado na maioria dos cenários.  
  
 "Exceção inesperada" geralmente não é uma exceção irrecuperável nem uma exceção de processamento; ele é, em vez disso, uma exceção inesperada do usuário. Uma exceção irrecuperável (por exemplo, uma exceção de falta de memória) – um geralmente tratados pelo [manipulador de exceção de modelo de serviço](http://msdn.microsoft.com/library/system.servicemodel.dispatcher.exceptionhandler.aspx) automaticamente – não é possível geralmente ser controladas muito bem e a única razão para lidar com tal uma exceção em todos os pode ser um log adicional ou para retornar uma exceção padrão para o cliente. Uma exceção de processamento ocorre no processamento da mensagem – por exemplo, na serialização, codificador ou nível de formatador – geralmente não pode ser tratada em um IErrorHandler, porque geralmente é muito cedo ou muito tarde para o manipulador de erro intervir por a hora em que essas exceções ocorrem. Da mesma forma, as exceções de transporte não podem ser tratadas em um IErrorHandler.  
  
 Com um IErrorHandler, você pode controlar explicitamente o comportamento do seu aplicativo quando uma exceção será lançada. Você pode:  
  
1.  Decida se deseja ou não enviar uma falha para o cliente  
  
2.  Substituir uma exceção com uma falha  
  
3.  Substituir uma falha por outra falha  
  
4.  Executar o registro em log ou rastreamento  
  
5.  Realizar outras atividades personalizadas  
  
 Um pode instalar um manipulador de erro personalizado adicionando-o à propriedade ErrorHandlers de distribuidores o canal para o serviço.  É possível ter mais de um manipulador de erros e eles são chamados na ordem em que eles são adicionados a esta coleção.  
  
 IErrorHandler.ProvideFault controla a mensagem de falha é enviada ao cliente. Este método é chamado, independentemente do tipo de exceção gerada por uma operação em seu serviço. Se nenhuma operação é executada aqui, o WCF assume seu comportamento padrão e continuará como não se houvesse nenhum manipulador de erro personalizada em vigor.  
  
 Uma área que talvez você pode usar essa abordagem é quando você deseja criar um local central para converter exceções em falhas antes de serem enviados ao cliente (garantindo que a instância não é descartada e o canal não é movido para o estado com falha).  
  
 O método IErrorHandler.HandleError normalmente é usado para implementar o erro comportamentos relacionados como erro de log de notificações do sistema, desligar o aplicativo, etc. IErrorHandler.HandleError pode ser chamado em vários locais dentro do serviço e, dependendo de onde o erro é gerado, o método HandleError pode ou não pode ser chamado pelo mesmo thread que a operação. Não há garantias nesse sentido.  
  
### <a name="dealing-with-exceptions-outside-wcf"></a>Tratamento de exceções fora do WCF  
 Geralmente, exceções de configuração, exceções de cadeia de caracteres de conexão do banco de dados e outras exceções semelhantes podem ocorrer dentro do contexto de um aplicativo WCF, mas não são exceções causadas por modelo de serviço ou o próprio serviço web. Essas exceções são externos ao serviço web de exceções "normais" e devem ser tratadas como outras exceções externas no ambiente devem ser manipulados.  
  
### <a name="tracing-exceptions"></a>Exceções de rastreamento  
 O rastreamento é o lugar de apenas "pega-tudo" onde um potencialmente pode ver todas as exceções. Para obter mais informações sobre exceções de registro em log e rastreamento, consulte o rastreamento e o registro.  
  
### <a name="uri-template-errors-when-using-webgetattribute-and-webinvokeattribute"></a>Erros de modelo URI ao usar o WebGetAttribute e o WebInvokeAttribute  
 Os atributos WebGet e WebInvoke permitem que você especifique um modelo de URI que mapeia os componentes do endereço da solicitação para parâmetros de operação. Por exemplo, o modelo de URI "clima / {estado} / {cidade}" mapeia o endereço de solicitação em tokens literais, um parâmetro denominado estado e um parâmetro denominado Cidade. Esses parâmetros, em seguida, podem ser associados por nome, para alguns dos parâmetros formais da operação.  
  
 Os parâmetros de modelo aparecem na forma de cadeias de caracteres no URI, enquanto os parâmetros formais de um contrato com tipo podem ser de tipos de cadeia de caracteres não. Portanto, uma conversão deve ocorrer antes da operação pode ser invocada. Um [tabela de conversão formatos](http://msdn.microsoft.com/library/bb412172.aspx) está disponível.  
  
 No entanto, se a conversão falhar, então não é possível informar a operação que algo deu errado. Em vez disso, a conversão de tipo revela na forma de uma falha de expedição.  
  
 Uma falha de expedição de conversão de tipo pode ser inspecionado mesmo assim como acontece com muitos outros tipos de falhas na expedição instalando um manipulador de erro. O ponto de extensibilidade IErrorHandler é chamado para manipular exceções de nível de serviço. A partir daí, a resposta a ser enviada de volta ao chamador –, bem como executar tarefas personalizadas e relatórios – pode ser escolhida.  
  
## <a name="see-also"></a>Consulte também  
 [Tratamento de erros do WCF básico](http://msdn.microsoft.com/library/gg281715.aspx)
