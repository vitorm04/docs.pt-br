---
title: "Exceções em threads gerenciados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- unhandled exceptions,in managed threads
- threading [.NET Framework],unhandled exceptions
- threading [.NET Framework],exceptions in managed threads
- managed threading
ms.assetid: 11294769-2e89-43cb-890e-ad4ad79cfbee
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ebb5559d300bb3db34fe640e87eb8b9e67931561
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="exceptions-in-managed-threads"></a>Exceções em threads gerenciados
Iniciando com o .NET Framework versão 2.0, o common language runtime permite mais exceções sem tratamento em threads para continuar naturalmente. Na maioria dos casos, isso significa que a exceção não tratada faz com que o aplicativo seja finalizado.  
  
> [!NOTE]
>  Essa é uma alteração significativa das versões do .NET Framework 1.0 e 1.1, que fornecem uma barreira para exceções não tratadas muitos — por exemplo, exceções não tratadas em threads de pool. Consulte [alterar de versões anteriores](#ChangeFromPreviousVersions) mais adiante neste tópico.  
  
 O common language runtime fornece exceções uma barreira para determinados sem tratamento que são usados para controlar o fluxo do programa:  
  
-   Um <xref:System.Threading.ThreadAbortException> é gerada em um thread porque <xref:System.Threading.Thread.Abort%2A> foi chamado.  
  
-   Um <xref:System.AppDomainUnloadedException> é gerada em um thread porque o domínio de aplicativo no qual o thread está em execução está sendo descarregado.  
  
-   O common language runtime ou um processo de host encerra o thread lançando uma exceção interna.  
  
 Se qualquer uma dessas exceções são sem tratamento em threads criados pelo common language runtime, a exceção encerra o thread, mas o common language runtime não permitir a exceção prossiga.  
  
 Se essas exceções sem tratamento no thread principal ou em threads que inseriu o tempo de execução de código não gerenciado, eles prosseguir normalmente, resultando no encerramento do aplicativo.  
  
> [!NOTE]
>  É possível que o tempo de execução lançar uma exceção não tratada, antes de qualquer código gerenciado tenha tido a oportunidade de instalar um manipulador de exceção. Mesmo se o código gerenciado não tivesse nenhuma possibilidade de manipular tal exceção, a exceção é permitida para prosseguir naturalmente.  
  
## <a name="exposing-threading-problems-during-development"></a>Expondo Threading problemas durante o desenvolvimento  
 Quando os threads podem falhar em modo silencioso, sem encerrar o aplicativo, graves problemas de programação podem não ser detectados. Este é um problema específico para serviços e outros aplicativos que são executados por longos períodos. Como threads falhar, estado do programa gradualmente torna-se corrompido. Pode degradar o desempenho do aplicativo ou o aplicativo pode travar.  
  
 Permitir exceções sem tratamento em threads para continuar naturalmente, até que o sistema operacional encerra o programa, expõe esses problemas durante o desenvolvimento e teste. Relatórios de erros no programa encerramentos suporte a depuração.  
  
<a name="ChangeFromPreviousVersions"></a>   
## <a name="change-from-previous-versions"></a>Alterar de versões anteriores  
 A alteração mais significativa se refere ao threads gerenciados. Nas versões do .NET Framework 1.0 e 1.1, o common language runtime fornece uma barreira para exceções não tratadas nas seguintes situações:  
  
-   Não há nenhum algo como uma exceção sem tratamento em um pool de threads. Quando uma tarefa gera uma exceção que não processa, o tempo de execução imprime o rastreamento de pilha de exceção para o console e, em seguida, retorna o thread para o pool de threads.  
  
-   Existe sem uma exceção sem tratamento em um thread criado com o <xref:System.Threading.Thread.Start%2A> método o <xref:System.Threading.Thread> classe. Quando o código em execução em um thread tal gera uma exceção que não processa, o tempo de execução imprime o rastreamento de pilha de exceção para o console e, em seguida, encerra normalmente o thread.  
  
-   Não há nenhum algo como uma exceção sem tratamento no thread do finalizador. Quando um finalizador gera uma exceção que não processa, o tempo de execução imprime o rastreamento de pilha de exceção para o console e, em seguida, permite que o thread do finalizador continuar a execução finalizadores.  
  
 O status de primeiro plano ou plano de fundo de um thread gerenciado não afeta esse comportamento.  
  
 Para obter exceções sem tratamento em threads de origem em código não gerenciado, a diferença é mais sutil. A caixa de diálogo do tempo de execução de anexação JIT impede a caixa de diálogo do sistema operacional para exceções gerenciadas ou nativo exceções em threads que passaram por código nativo. O processo termina em todos os casos.  
  
### <a name="migrating-code"></a>Migrando o código  
 Em geral, a alteração irá expor anteriormente não reconhecido de problemas de programação para que eles possam ser corrigidos. Em alguns casos, no entanto, os programadores podem aproveitam a proteção em tempo de execução, por exemplo, para encerrar threads. Dependendo da situação, eles devem considerar uma das seguintes estratégias de migração:  
  
-   Reestruture o código para que o thread será fechado normalmente quando um sinal.  
  
-   Use o <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> método para anular o thread.  
  
-   Se um thread deve ser interrompido para que o encerramento do processo pode continuar, verifique o thread de um thread em segundo plano para que ela será encerrada automaticamente no encerramento do processo.  
  
 Em todos os casos, a estratégia deve seguir as diretrizes de design para exceções. Consulte [diretrizes de Design para exceções](../../../docs/standard/design-guidelines/exceptions.md).  
  
### <a name="application-compatibility-flag"></a>Sinalizador de compatibilidade do aplicativo  
 Como uma medida temporária de compatibilidade, os administradores podem colocar um sinalizador de compatibilidade no `<runtime>` seção do arquivo de configuração do aplicativo. Isso faz com que o common language runtime reverter para o comportamento de versões 1.0 e 1.1.  
  
```xml  
<legacyUnhandledExceptionPolicy enabled="1"/>  
```  
  
## <a name="host-override"></a>Substituição do host  
 No .NET Framework versão 2.0, um host não gerenciado pode usar o [ICLRPolicyManager](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md) interface na API de hospedagem para substituir o padrão de política de exceções do common language runtime não tratada. O [: SetUnhandledExceptionPolicy](../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-setunhandledexceptionpolicy-method.md) função é usada para definir a política para exceções não tratadas.  
  
## <a name="see-also"></a>Consulte também  
 [Noções básicas de threading gerenciado](../../../docs/standard/threading/managed-threading-basics.md)
