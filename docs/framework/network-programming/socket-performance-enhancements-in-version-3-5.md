---
title: Melhorias do desempenho de soquete na versão 3.5
ms.date: 03/30/2017
ms.assetid: 225aa5f9-c54b-4620-ab64-5cd100cfd54c
author: mcleblanc
ms.author: markl
ms.openlocfilehash: ddf098d0da7411515592c5bfa5bbac2153d7f0eb
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47197106"
---
# <a name="socket-performance-enhancements-in-version-35"></a>Melhorias do desempenho de soquete na versão 3.5
A classe <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> foi aprimorada na Versão 3.5 para uso por aplicativos que usam a E/S de rede assíncrona para obter o melhor desempenho. Uma série de novas classes foi adicionada como parte de um conjunto de melhorias da classe <xref:System.Net.Sockets.Socket>, que fornece um padrão assíncrono alternativo que pode ser usado por aplicativos de soquete especializados de alto desempenho. Essas melhorias foram projetadas especificamente para aplicativos de servidor de rede que exigem alto desempenho. Um aplicativo pode usar o padrão assíncrono aprimorado exclusivamente ou somente nas áreas de acesso direcionadas de seu aplicativo (ao receber grandes quantidades de dados, por exemplo).  
  
## <a name="class-enhancements"></a>Melhorias da classe  
 O principal recurso dessas melhorias é evitar a alocação e a sincronização repetidas de objetos durante a E/S de soquete assíncrono de alto volume. O padrão de design Início/Fim atualmente implementado pela classe <xref:System.Net.Sockets.Socket> para a E/S de soquete assíncrono exige que um objeto <xref:System.IAsyncResult?displayProperty=nameWithType> seja alocado para cada operação de soquete assíncrono.  
  
 Nas novas melhorias da classe <xref:System.Net.Sockets.Socket>, as operações de soquete assíncrono são descritas por objetos da classe <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType> reutilizáveis alocados e mantidos pelo aplicativo. Os aplicativos de soquete de alto desempenho sabem muito bem a quantidade de operações de soquete sobreposto que devem ser sustentadas. O aplicativo pode criar a quantidade de objetos <xref:System.Net.Sockets.SocketAsyncEventArgs> de que precisar. Por exemplo, se um aplicativo para servidores precisar ter 15 operações de aceitação de soquete pendentes em todos os momentos para dar suporte às taxas de conexão de cliente de entrada, ele poderá alocar 15 objetos <xref:System.Net.Sockets.SocketAsyncEventArgs> reutilizáveis com antecedência para essa finalidade.  
  
 O padrão para executar uma operação de soquete assíncrono com essa classe consiste nas seguintes etapas:  
  
1.  Alocar um novo objeto de contexto <xref:System.Net.Sockets.SocketAsyncEventArgs> ou obter um gratuito em um pool de aplicativos.  
  
2.  Definir as propriedades no objeto de contexto para a operação prestes a ser executada (o método de representante do retorno de chamada e o buffer de dados, por exemplo).  
  
3.  Chamar o método de soquete apropriado (xxxAsync) para iniciar a operação assíncrona.  
  
4.  Se o método de soquete assíncrono (xxxAsync) retornar verdadeiro no retorno de chamada, consulte as propriedades do contexto para obter o status de conclusão.  
  
5.  Se o método de soquete assíncrono (xxxAsync) retornar falso no retorno de chamada, isso indicará que a operação foi concluída de forma síncrona. As propriedades do contexto podem ser consultadas para obter o resultado da operação.  
  
6.  Reutilizar o contexto para outra operação, colocá-lo novamente no pool ou descartá-lo.  
  
 O tempo de vida do novo objeto de contexto da operação de soquete assíncrono é determinado por referências no código do aplicativo e por referências de E/S assíncrona. Não é necessário que o aplicativo retenha uma referência a um objeto de contexto da operação de soquete assíncrono depois que ele é enviado como um parâmetro para um dos métodos da operação de soquete assíncrono. Ele permanecerá referenciado até o retorno do retorno de chamada de conclusão. No entanto, é vantajoso para o aplicativo reter a referência ao objeto de contexto, de modo que ele possa ser reutilizado para uma operação futura de soquete assíncrono.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SendPacketsElement?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncEventArgs?displayProperty=nameWithType>  
 <xref:System.Net.Sockets.SocketAsyncOperation?displayProperty=nameWithType>  
 [Amostras de programação de rede](../../../docs/framework/network-programming/network-programming-samples.md)  
 [Exemplos de código de soquete](socket-code-examples.md)
