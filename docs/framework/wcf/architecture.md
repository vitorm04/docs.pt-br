---
title: Arquitetura do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: b0e4f9af0ff84a8d560b332d227b1ba9ae18bd4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782442"
---
# <a name="windows-communication-foundation-architecture"></a>Arquitetura do Windows Communication Foundation
O gráfico a seguir ilustra as principais camadas da arquitetura do Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Arquitetura do WCF  
 ![Arquitetura do WCF](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Contratos e descrições  
 Contratos definem os vários aspectos do sistema de mensagens. O contrato de dados descreve cada parâmetro que compõe a todas as mensagens que um serviço pode criar ou consumir. Os parâmetros da mensagem são definidos por documentos de idioma (XSD) de definição de esquema XML, permitindo que qualquer sistema que ele compreenda XML para processar os documentos. O contrato de mensagem define partes de mensagem específica usando protocolos SOAP e permite controle refinado sobre partes da mensagem, quando tal precisão de demanda de interoperabilidade. O contrato de serviço Especifica as assinaturas de método reais do serviço e é distribuído como uma interface em uma das linguagens de programação com suporte, como Visual Basic ou Visual C#.  
  
 As políticas e associações estipulam as condições necessárias para se comunicar com um serviço.  Por exemplo, a associação (no mínimo) Especifique o transporte usado (por exemplo, HTTP ou TCP) e uma codificação. Políticas incluem requisitos de segurança e outras condições que devem ser atendidas para se comunicar com um serviço.  
  
### <a name="service-runtime"></a>Tempo de execução do serviço  
 Camada de serviço de tempo de execução contém os comportamentos que ocorrem apenas durante a operação real do serviço, ou seja, os comportamentos de tempo de execução do serviço. A limitação controles quantas mensagens são processadas, que pode ser variado se a demanda para o serviço cresce até um limite predefinido. Um comportamento de erro Especifica o que ocorre quando ocorre um erro interno no serviço, por exemplo, controlando quais informações são comunicadas ao cliente. (Informações demais podem dar a um usuário mal-intencionado uma vantagem na montagem de um ataque.) Controla o comportamento de metadados como e se os metadados são disponibilizados para o mundo exterior. Comportamento da instância Especifica quantas instâncias do serviço podem ser executadas (por exemplo, um singleton especifica apenas uma instância para processar todas as mensagens). Comportamento de transação permite a reversão de operações realizadas, se ocorrer uma falha. Comportamento de expedição é o controle de como uma mensagem é processada pela infraestrutura do WCF.  
  
 Extensibilidade permite a personalização dos processos de tempo de execução. Por exemplo, inspeção das mensagens é a facilidade para inspecionar as partes de uma mensagem e a filtragem de parâmetro permite ações predefinidas para ocorrer com base em filtros atuando em cabeçalhos de mensagem.  
  
### <a name="messaging"></a>Mensagens  
 A camada de mensagens é composta *canais*. Um canal é um componente que processa uma mensagem de alguma forma, por exemplo, por meio da autenticação de uma mensagem. Um conjunto de canais é também conhecido como um *pilha de canais*. Canais de operam em mensagens e cabeçalhos de mensagem. Isso é diferente da camada de tempo de execução de serviço, que seja principalmente preocupada sobre como processar o conteúdo de corpos de mensagens.  
  
 Há dois tipos de canais: canais e canais de protocolo de transporte.  
  
 Canais de transporte de ler e gravem mensagens de rede (ou algum outro ponto de comunicação com o mundo exterior). Alguns transportes usarem um codificador para converter mensagens (que são representadas como XML Infosets) e para a representação de fluxo de bytes usado pela rede. Exemplos de transportes são HTTP, pipes nomeados, TCP e MSMQ. São exemplos de codificações XML e binários otimizados.  
  
 Canais de protocolo implementam protocolos de processamento de mensagem, muitas vezes lendo ou gravando cabeçalhos adicionais para a mensagem. WS-Security e WS-confiabilidade são exemplos de tais protocolos.  
  
 A camada de mensagens ilustra os possíveis formatos e padrões de troca de dados. WS-Security é uma implementação da especificação de WS-Security e habilitar a segurança na camada de mensagem. O canal de mensagens WS-Reliable permite que a garantia de entrega de mensagens. Os codificadores apresentam uma variedade de codificações que podem ser usadas para atender às necessidades da mensagem. O canal HTTP Especifica que o protocolo de transporte de hipertexto é usado para entrega de mensagens. Da mesma forma, o canal TCP Especifica o protocolo TCP. O canal de fluxo de transação controla os padrões de mensagens transacionadas. O canal de Pipe nomeado permite a comunicação entre processos. O canal MSMQ permite interoperação com aplicativos MSMQ.  
  
### <a name="hosting-and-activation"></a>Hospedagem e ativação  
 Em sua forma final, um serviço é um programa. Como outros programas, um serviço deve ser executado em um executável. Isso é conhecido como um *auto-hospedado* service.  
  
 Os serviços também podem ser *hospedado*, ou executar em um executável gerenciado por um agente externo, como o IIS ou o Windows Activation Service (WAS). ERA permite que os aplicativos WCF seja ativado automaticamente quando implantado em um computador em execução. Os serviços também podem ser executados manualmente como executáveis (arquivos .exe). Um serviço também pode ser executado automaticamente como um serviço do Windows. Componentes COM+ também podem ser hospedados como serviços WCF.  
  
## <a name="see-also"></a>Consulte também

- [O que é o Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Conceitos fundamentais do Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
