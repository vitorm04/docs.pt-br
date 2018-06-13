---
title: Arquitetura do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: 1514010ca573be364e54a53ae047a2ff49cdad82
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804216"
---
# <a name="windows-communication-foundation-architecture"></a>Arquitetura do Windows Communication Foundation
O gráfico a seguir ilustra as camadas principais da arquitetura do Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Arquitetura do WCF  
 ![A arquitetura do WCF](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Contratos e descrições  
 Contratos definem os vários aspectos do sistema de mensagens. O contrato de dados descreve cada parâmetro que compõe a cada mensagem que um serviço pode criar ou consumir. Os parâmetros de mensagem são definidos por documentos de linguagem XSD de definição de esquema XML, permitindo a qualquer sistema que entenda XML para processar os documentos. O contrato de mensagem define partes de mensagem específica usando protocolos SOAP e permite controle refinado sobre partes da mensagem, quando tal precisão demandas de interoperabilidade. O contrato de serviço Especifica as assinaturas de método real do serviço e é distribuído como uma interface em uma das linguagens de programação com suporte, como Visual Basic ou Visual c#.  
  
 As políticas e associações estipulam as condições necessárias para se comunicar com um serviço.  Por exemplo, a associação (no mínimo) Especifique o transporte usado (por exemplo, HTTP ou TCP) e uma codificação. As políticas incluem requisitos de segurança e outras condições que devem ser atendidas para se comunicar com um serviço.  
  
### <a name="service-runtime"></a>Tempo de execução do serviço  
 A camada de serviço em tempo de execução contém os comportamentos que ocorrem apenas durante a operação real do serviço, ou seja, os comportamentos de tempo de execução do serviço. Limitação controla quantas mensagens são processadas, que podem ser variado se aumenta a demanda para o serviço para um limite predefinido. Um comportamento de erro Especifica o que acontece quando ocorre um erro interno no serviço, por exemplo, controlando quais informações são comunicadas ao cliente. (Muitas informações podem dar a um usuário mal-intencionado uma vantagem de um ataque de montagem.) Controla o comportamento de metadados como e se os metadados é disponibilizado para o mundo exterior. Comportamento da instância Especifica quantas instâncias do serviço podem ser executadas (por exemplo, um singleton especifica apenas uma instância para processar todas as mensagens). Comportamento de transação permite a reversão de operações realizadas se ocorrer uma falha. Comportamento de distribuição é o controle de como uma mensagem é processada pela infraestrutura do WCF.  
  
 Extensibilidade permite personalização de processos de tempo de execução. Por exemplo, inspeção de mensagem é a facilidade de inspecionar as partes de uma mensagem e a filtragem de parâmetro permite que a predefinição ações que devem ocorrer com base em filtros atuando em cabeçalhos de mensagem.  
  
### <a name="messaging"></a>Mensagens  
 A camada de mensagens é composta de *canais*. Um canal é um componente que processa uma mensagem de alguma forma, por exemplo, autenticação de uma mensagem. Um conjunto de canais é também conhecido como um *pilha de canais*. Canais operam em mensagens e cabeçalhos de mensagem. Isso é diferente da camada de tempo de execução de serviço, que se concentra-se sobre o conteúdo do corpo da mensagem de processamento.  
  
 Há dois tipos de canais: canais e canais de protocolo de transporte.  
  
 Canais de transporte ler e gravem mensagens de rede (ou algum outro ponto de comunicação com o mundo exterior). Alguns transportes usarem um codificador converter mensagens (que são representadas como XML Infosets) de e para a representação de fluxo de bytes usado pela rede. Exemplos de transportes são HTTP, pipes nomeados, TCP e MSMQ. São exemplos de codificações de XML e binários otimizado.  
  
 Canais de protocolo para implementar protocolos de processamento de mensagens, geralmente, ler ou gravar cabeçalhos adicionais para a mensagem. WS-Security e WS-confiabilidade são exemplos de tais protocolos.  
  
 A camada de mensagens ilustra os possíveis formatos e os padrões de troca de dados. WS-Security é uma implementação da especificação WS-Security, habilitando a segurança na camada de mensagem. O canal de mensagens WS-Reliable habilita a garantia de entrega de mensagens. Os codificadores apresentam uma variedade de codificações que podem ser usadas para se adequar às necessidades da mensagem. O canal HTTP Especifica que o protocolo de transporte é usado para entrega de mensagens. Da mesma forma, o canal TCP Especifica o protocolo TCP. O canal de fluxo de transação rege padrões de mensagens transacionadas. O canal de Pipe nomeado permite a comunicação entre processos. O canal MSMQ permite interoperação com os aplicativos MSMQ.  
  
### <a name="hosting-and-activation"></a>Ativação e hospedagem  
 Em sua forma final, um serviço é um programa. Como outros programas, um serviço deve ser executado em um executável. Isso é conhecido como um *auto-hospedado* serviço.  
  
 Serviços também podem ser *hospedado*, ou executar um executável gerenciado por um agente externo, como o IIS ou o serviço de ativação do Windows (WAS). ERA permite que os aplicativos WCF seja ativada automaticamente quando implantado em um computador que está executando. Os serviços também podem ser executados manualmente como executáveis (arquivos .exe). Um serviço também pode ser executado automaticamente como um serviço do Windows. Componentes COM+ também podem ser hospedados como serviços WCF.  
  
## <a name="see-also"></a>Consulte também  
 [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Conceitos fundamentais do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
