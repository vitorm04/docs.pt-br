---
title: Azure Monitor
description: O uso do Monitor Azure para ganhar visibilidade no sistema está sendo executado.
ms.date: 02/05/2020
ms.openlocfilehash: 4e5ddba6c1c13dc65662a7748d4ae3a58a6a6f68
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805624"
---
# <a name="azure-monitor"></a>Azure Monitor

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Nenhum outro provedor de nuvem tem uma solução de monitoramento de aplicativos em nuvem tão madura quanto a encontrada no Azure. O Azure Monitor é um nome guarda-chuva para uma coleção de ferramentas projetadas para fornecer visibilidade sobre o estado do seu sistema, insights sobre quaisquer problemas e otimização do seu aplicativo.

![O Azure Monitor, uma coleção de ferramentas para fornecer informações sobre como um aplicativo nativo da nuvem está funcionando. ](./media/azure-monitor.png)
 **Figura 7-12**. O Azure Monitor, uma coleção de ferramentas para fornecer informações sobre como um aplicativo nativo da nuvem está funcionando.

## <a name="gathering-logs-and-metrics"></a>Coleta de registros e métricas

O primeiro passo em qualquer solução de monitoramento é reunir o máximo de dados possível. Quanto mais dados podem ser coletados, mais profundos são os insights que podem ser obtidos. Os sistemas de instrumentação têm sido tradicionalmente difíceis. O Simples Protocolo de Gerenciamento de Rede (SNMP) era o protocolo padrão-ouro para coletar informações de nível de máquina, mas exigia muito conhecimento e configuração. Felizmente, grande parte desse trabalho duro foi eliminada, pois as métricas mais comuns são coletadas automaticamente pelo Azure Monitor.

Métricas e eventos de nível de aplicação não são possíveis de instrumentar automaticamente porque são específicos para o aplicativo que está sendo implantado. Para coletar essas métricas, [existem SDKs e APIs disponíveis](https://docs.microsoft.com/azure/azure-monitor/app/api-custom-events-metrics) para relatar diretamente essas informações, como quando um cliente se inscreve ou completa um pedido. As exceções também podem ser capturadas e reportadas de volta ao Azure Monitor via Application Insights. Os SDKs suportam a maioria das linguagens encontradas em aplicativos nativos da nuvem, incluindo go, python, javascript e os idiomas .NET.

O objetivo final de coletar informações sobre o estado do seu aplicativo é garantir que seus usuários finais tenham uma boa experiência. Que melhor maneira de saber se os usuários estão enfrentando problemas do que fazendo [testes web externos?](https://docs.microsoft.com/azure/azure-monitor/app/monitor-web-app-availability) Esses testes podem ser tão simples quanto pingar seu site de locais ao redor do mundo ou tão envolvidos quanto ter agentes locomisso no site e simular ações do usuário.

## <a name="reporting-data"></a>Relatórios de dados

Uma vez que os dados são coletados, eles podem ser manipulados, resumidos e plotados em gráficos, que permitem que os usuários vejam instantaneamente quando há problemas. Esses gráficos podem ser reunidos em dashboards ou em Workbooks, um relatório de várias páginas projetado para contar uma história sobre algum aspecto do sistema.

Nenhuma aplicação moderna seria completa sem alguma inteligência artificial ou aprendizado de máquina. Para isso, os dados [podem ser passados](https://www.youtube.com/watch?v=Cuza-I1g9tw) para as várias ferramentas de aprendizado de máquina no Azure para permitir que você extraia tendências e informações que de outra forma estariam ocultadas.

O Application Insights fornece uma poderosa linguagem de consulta chamada Kusto que pode ser usada para encontrar registros, resumi-los e até mesmo gráficos de plot. Por exemplo, esta consulta localizará todos os registros do mês de novembro de 2007, os agrupará por estado e traçará o top 10 como um gráfico de tortas.

```kusto
StormEvents
| where StartTime >= datetime(2007-11-01) and StartTime < datetime(2007-12-01)
| summarize count() by State
| top 10 by count_
| render piechart
```

![O resultado da figura de](./media/azure-monitor.png)
consulta de insights do aplicativo**7-13**. O resultado da consulta de insights do aplicativo.

Há um playground para experimentar as consultas de [Kusto,](https://dataexplorer.azure.com/clusters/help/databases/Samples) que é um lugar fantástico para passar uma ou duas horas. A leitura [de consultas de amostra](https://docs.microsoft.com/azure/kusto/query/samples) também pode ser instrutiva.

## <a name="dashboards"></a>Painéis

Existem várias tecnologias de painel diferentes que podem ser usadas para emergir as informações do Azure Monitor. Talvez o mais simples seja apenas executar consultas no Application Insights e [plotar os dados em um gráfico](https://docs.microsoft.com/azure/azure-monitor/learn/tutorial-app-dashboards).

![Um exemplo de gráficos de insights de](./media/azure-monitor.png)
aplicativos incorporados na figura principal do painel do Azure**7-14**. Um exemplo de gráficos do Application Insights incorporados no painel principal do Azure.

Esses gráficos podem então ser incorporados no portal Azure propriamente dito através do uso do recurso de painel. Para usuários com requisitos mais exigentes, como ser capaz de detalhar em vários níveis de dados, os dados do Azure Monitor estão disponíveis para [o Power BI](https://powerbi.microsoft.com/). O Power BI é uma ferramenta líder do setor, classe empresarial, de inteligência empresarial que pode agregar dados de muitas fontes de dados diferentes.

![Um exemplo do](./media/azure-monitor.png)
painel power bi**figura 7-15**. Um exemplo de painel Power BI.

## <a name="alerts"></a>Alertas

Às vezes, ter dashboards de dados é insuficiente. Se ninguém está acordado para assistir aos painéis, então ainda pode levar muitas horas até que um problema seja resolvido, ou mesmo detectado. Para isso, o Azure Monitor também fornece uma [solução de alerta](https://docs.microsoft.com/azure/azure-monitor/platform/alerts-overview)de primeira linha . Os alertas podem ser acionados por uma ampla gama de condições, incluindo:

- Valores métricos
- Consultas da pesquisa de logs
- Eventos do Log de Atividades
- Integridade da plataforma subjacente do Azure
- Testes de disponibilidade do site

Quando acionados, os alertas podem executar uma grande variedade de tarefas. No lado simples, os alertas podem apenas enviar uma notificação de e-mail para uma lista de discussão ou uma mensagem de texto para um indivíduo. Alertas mais envolvidos podem desencadear um fluxo de trabalho em uma ferramenta como o PagerDuty, que está ciente de quem está de plantão para um determinado aplicativo. Os alertas podem desencadear ações no [Microsoft Flow](https://flow.microsoft.com/) desbloqueando possibilidades quase ilimitadas para fluxos de trabalho.

À medida que as causas comuns dos alertas são identificadas, os alertas podem ser aprimorados com detalhes sobre as causas comuns dos alertas e as medidas a serem tomadas para resolvê-los. Implantações de aplicativos nativas da nuvem altamente maduras podem optar por iniciar tarefas de auto-recuperação, que executam ações como remover nódulos falhados de um conjunto de escala ou desencadear uma atividade de autodimensionamento. Eventualmente, pode não ser mais necessário acordar o pessoal de plantão às 2h para resolver um problema no local, pois o sistema será capaz de se ajustar para compensar ou pelo menos mancar até que alguém chegue ao trabalho na manhã seguinte.

O Azure Monitor aproveita automaticamente o aprendizado de máquina para entender os parâmetros operacionais normais dos aplicativos implantados. Isso permite detectar serviços que estão operando fora de seus parâmetros normais. Por exemplo, o tráfego típico durante a semana no site pode ser de 10.000 solicitações por minuto. E então, em uma determinada semana, de repente o número de pedidos atinge um altamente incomum 20.000 pedidos por minuto. [A Detecção Inteligente](https://docs.microsoft.com/azure/azure-monitor/app/proactive-diagnostics) notará esse desvio da norma e acionará um alerta. Ao mesmo tempo, a análise de tendência é inteligente o suficiente para evitar disparar falsos positivos quando a carga de tráfego é esperada.

## <a name="references"></a>Referências

- [Azure Monitor](https://docs.microsoft.com/azure/azure-monitor/overview)

>[!div class="step-by-step"]
>[Próximo](monitoring-azure-kubernetes.md)
>[anterior](identity.md)
