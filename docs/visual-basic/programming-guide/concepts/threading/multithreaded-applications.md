---
title: "Aplicativos multithread (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
ms.assetid: 02b0444b-2e68-4f2c-bc28-28c046004017
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Aplicativos multithread (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Com o Visual Basic, você pode escrever aplicativos que executam várias tarefas ao mesmo tempo. Tarefas com o potencial de manter outras tarefas podem executar em segmentos separados, um processo conhecido como *multithreading* ou *livre threading*.  
  
 Aplicativos que usam multithreading são mais responsivo ao usuário de entrada porque a interface do usuário permanece ativa como executar tarefas de processamento intensivo em threads separados. Multithreading também é útil quando você cria aplicativos escalonáveis, porque você pode adicionar segmentos medida que aumenta a carga de trabalho.  
  
## Criando e usando Threads  
 Se você precisar de mais controle sobre o comportamento de threads do aplicativo, você pode gerenciar os threads por conta própria. No entanto, perceba que gravar aplicativos multithreaded corretos pode ser difícil: O aplicativo pode parar de responder ou experimentar erros transitórios causados pelas condições de corrida. Para obter mais informações, consulte [Thread\-Safe Components](../Topic/Thread-Safe%20Components.md).  
  
 Criar um novo thread, declarando uma variável do tipo <xref:System.Threading.Thread> e chamando o construtor, fornecendo o nome do procedimento ou método que você deseja executar no novo segmento. O código a seguir fornece um exemplo.  
  
```vb  
Dim newThread As New System.Threading.Thread(AddressOf AMethod)  
```  
  
### Iniciando e parando segmentos  
 Para iniciar a execução de um novo thread, use o <xref:System.Threading.Thread.Start%2A> método, conforme mostrado no código a seguir.  
  
```vb  
newThread.Start()  
```  
  
 Para interromper a execução de um thread, use o <xref:System.Threading.Thread.Abort%2A> método, conforme mostrado no código a seguir.  
  
```vb  
newThread.Abort()  
```  
  
 Além de iniciar e parar threads, você também pode pausar threads chamando o <xref:System.Threading.Thread.Sleep%2A> ou <xref:System.Threading.Thread.Suspend%2A> método, retome um thread suspenso usando o <xref:System.Threading.Thread.Resume%2A> método e destrua um thread usando o <xref:System.Threading.Thread.Abort%2A> método  
  
### Métodos de thread  
 A tabela a seguir mostra alguns dos métodos que você pode usar para controlar segmentos individuais.  
  
|Método|Ação|  
|------------|----------|  
|<xref:System.Threading.Thread.Start%2A>|Faz com que um segmento comece a executar.|  
|<xref:System.Threading.Thread.Sleep%2A>|Pausa um segmento por um período especificado.|  
|<xref:System.Threading.Thread.Suspend%2A>|Pausa um segmento quando ele atinge um ponto de segurança.|  
|<xref:System.Threading.Thread.Abort%2A>|Pára um segmento quando ele atinge um ponto de segurança.|  
|<xref:System.Threading.Thread.Resume%2A>|Reinicia um segmento suspenso|  
|<xref:System.Threading.Thread.Join%2A>|Faz com que o thread atual aguardar outro thread seja finalizado. Se usado com um valor de tempo limite, este método retorna `True` se o segmento termina no tempo alocado.|  
  
### Pontos seguros  
 A maioria desses métodos são auto\-explicativos, mas o conceito de *pontos seguros* pode ser novidade para você. Pontos de segurança são locais no código onde é seguro para o common language runtime executar automático *coleta de lixo*, o processo de liberação de variáveis não utilizadas e recuperação de memória. Quando você chama o <xref:System.Threading.Thread.Abort%2A> ou <xref:System.Threading.Thread.Suspend%2A> método de um segmento, o common language runtime analisa o código e determina um local apropriado para o thread parar a execução.  
  
### Propriedades de thread  
 Segmentos também contêm diversas propriedades úteis, como mostrado na tabela a seguir:  
  
|Propriedade|Valor|  
|-----------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Contém o valor `True` se um thread estiver ativo.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Obtém ou define um valor booleano que indica se um thread está ou deve ser um thread em segundo plano. Threads de plano de fundo são como segmentos de primeiro plano, mas um thread em segundo plano não impede que um processo de parada. Depois que todos os threads de primeiro plano que pertencem a um processo forem interrompidos, o common language runtime finaliza o processo chamando o <xref:System.Threading.Thread.Abort%2A> método em threads de plano de fundo que ainda está ativo.|  
|<xref:System.Threading.Thread.Name%2A>|Obtém ou define o nome de um thread. Usados com mais freqüência para descobrir segmentos individuais quando você depura.|  
|<xref:System.Threading.Thread.Priority%2A>|Obtém ou define um valor que é usado pelo sistema operacional para priorizar agendamento de segmento.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Contém um valor que descreve o estado ou estados de um thread.|  
  
## Prioridades do thread  
 Cada thread tem uma propriedade de prioridade que determina como grande ou pequena uma fatia de tempo do processador ele tem para executar. O sistema operacional aloca frações de tempo maiores para segmentos de alta prioridade e frações de tempo mais curtas para segmentos de baixa prioridade. Novos segmentos são criados com o valor de `Normal`, mas você pode alterar o <xref:System.Threading.Thread.Priority%2A> propriedade para qualquer valor na <xref:System.Threading.ThreadPriority> enumeração.  
  
 Consulte <xref:System.Threading.ThreadPriority> para obter uma descrição detalhada sobre as várias prioridades do thread.  
  
## Threads em primeiro plano e em segundo plano  
 Um *segmento do primeiro plano* executa indefinidamente, enquanto um *thread de segundo plano* pára assim que o último segmento do primeiro plano foi interrompido. Você pode usar o <xref:System.Threading.Thread.IsBackground%2A> propriedade para determinar ou alterar o status do plano de fundo de um thread.  
  
## Consulte também  
 <xref:System.Threading.Thread>   
 [Sincronização de thread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/thread-synchronization.md)   
 [Parâmetros e valores de retorno para procedimentos multithread \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/parameters-and-return-values-for-multithreaded-procedures.md)   
 [Threading \(Visual Basic\)](../../../../visual-basic/programming-guide/concepts/threading/index.md)