---
title: Suporte para consultas
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 5c46ed5ae2fc2cc2275bfa7251fe5f8fa346c1f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="support-for-queries"></a>Suporte para consultas
A instância Store de fluxo de trabalho do SQL registra um conjunto de propriedades conhecidos no armazenamento. Os usuários podem ver para as instâncias com base nessas propriedades. A lista a seguir contém algumas dessas propriedades conhecidas:  
  
-   **Nome do site.** Nome do site que contém o serviço.  
  
-   **Caminho relativo de aplicativo.** Caminho do aplicativo relativa ao site.  
  
-   **Caminho relativo do serviço.** Caminho do serviço relativo para o aplicativo.  
  
-   **Nome do serviço.** Nome do serviço.  
  
-   **Namespace de serviço.** Nome do namespace que usa o serviço.  
  
-   **Computador atual.**  
  
-   **Máquina de última**. O computador no qual a instância do serviço de fluxo de trabalho executou a última vez.  
  
> [!NOTE]
>  Para cenários são hospedados usando o host de Serviço de Fluxo de Trabalho, somente as quatro propriedades mais recentes são preenchidas. Para cenários de aplicativo de fluxo de trabalho, apenas a propriedade a última é preenchida.  
  
 O tempo de execução de fluxo de trabalho fornece valores para as primeiras três propriedades. O host de serviço de fluxo de trabalho fornece o valor para o **motivo suspender** propriedade. O armazenamento de instância de fluxo de trabalho do SQL em si fornece valores para o **última máquina atualizado** propriedade.  
  
 O recurso de Store de instância de fluxo de trabalho do SQL também permite que você especifique as propriedades personalizadas que você deseja armazenar os valores na base de dados de persistência e que você deseja usar em consultas. Para obter mais informações sobre promoções personalizadas, consulte [repositório extensibilidade](../../../docs/framework/windows-workflow-foundation/store-extensibility.md).  
  
## <a name="views"></a>Exibições  
 O armazenamento de instância contém as seguintes modos de exibição. Consulte [esquema de banco de dados de persistência](../../../docs/framework/windows-workflow-foundation/persistence-database-schema.md) para obter mais detalhes.  
  
### <a name="the-instances-view"></a>O modo de instâncias  
 O modo de instâncias contém os campos seguintes:  
  
1.  **Id**  
  
2.  **PendingTimer**  
  
3.  **CreationTime**  
  
4.  **LastUpdatedTime**  
  
5.  **ServiceDeploymentId**  
  
6.  **SuspensionExceptionName**  
  
7.  **SuspensionReason**  
  
8.  **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>O modo de ServiceDeployments  
 O modo de ServiceDeployments contém os campos seguintes:  
  
1.  **Nome do site**  
  
2.  **RelativeServicePath**  
  
3.  **RelativeApplicationPath**  
  
4.  **ServiceName**  
  
5.  **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>O modo de InstancePromotedProperties  
 O modo de InstancePromotedProperties contém os seguintes campos. Para obter detalhes sobre propriedades promovidas, consulte o [repositório extensibilidade](../../../docs/framework/windows-workflow-foundation/store-extensibility.md) tópico.  
  
1.  **instanceId**  
  
2.  **EncodingOption**  
  
3.  **PromotionName**  
  
4.  **Valor #** (um conjunto de campos de **Value1** para **Value64**).
