---
title: Suporte para consultas
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: e281b5ae7a41bd282f8e7c7eb9db6f99ef5487f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948932"
---
# <a name="support-for-queries"></a>Suporte para consultas
A instância Store de fluxo de trabalho do SQL registra um conjunto de propriedades conhecidos no armazenamento. Os usuários podem ver para as instâncias com base nessas propriedades. A lista a seguir contém algumas dessas propriedades conhecidas:  
  
- **Nome do site.** Nome do site que contém o serviço.  
  
- **Caminho de aplicativo relativo.** Caminho do aplicativo relativa ao site.  
  
- **Caminho de serviço relativo.** Caminho do serviço relativo para o aplicativo.  
  
- **Nome do serviço.** Nome do serviço.  
  
- **Namespace de serviço.** Nome do namespace que usa o serviço.  
  
- **Computador atual.**  
  
- **Última máquina**. O computador no qual a instância do serviço de fluxo de trabalho executou a última vez.  
  
> [!NOTE]
> Para cenários são hospedados usando o host de Serviço de Fluxo de Trabalho, somente as quatro propriedades mais recentes são preenchidas. Para cenários de aplicativo de fluxo de trabalho, apenas a propriedade a última é preenchida.  
  
 O tempo de execução de fluxo de trabalho fornece valores para as primeiras três propriedades. O host do serviço de fluxo de trabalho fornece o valor para a propriedade do **motivo da suspensão** . A instância do fluxo de trabalho SQL armazena a si mesma fornece valores para a última propriedade de **computador atualizada** .  
  
 O recurso de Store de instância de fluxo de trabalho do SQL também permite que você especifique as propriedades personalizadas que você deseja armazenar os valores na base de dados de persistência e que você deseja usar em consultas. Para obter mais informações sobre promoções personalizadas, consulte [extensibilidade de armazenamento](store-extensibility.md).  
  
## <a name="views"></a>Exibições  
 O armazenamento de instância contém as seguintes modos de exibição. Confira [esquema do banco de dados de persistência](persistence-database-schema.md) para obter mais detalhes.  
  
### <a name="the-instances-view"></a>O modo de instâncias  
 O modo de instâncias contém os campos seguintes:  
  
1. **ID**  
  
2. **PendingTimer**  
  
3. **CreationTime**  
  
4. **LastUpdatedTime**  
  
5. **ServiceDeploymentId**  
  
6. **SuspensionExceptionName**  
  
7. **SuspensionReason**  
  
8. **ActiveBookmarks**  
  
9. **CurrentMachine**  
  
10. **LastMachine**  
  
11. **ExecutionStatus**  
  
12. **IsInitialized**  
  
13. **IsSuspended**  
  
14. **Membros IsCompleted**  
  
15. **EncodingOption**  
  
16. **ReadWritePrimitiveDataProperties**  
  
17. **WriteOnlyPrimitiveDataProperties**  
  
18. **ReadWriteComplexDataProperties**  
  
19. **WriteOnlyComplexDataProperties**  
  
### <a name="the-servicedeployments-view"></a>O modo de ServiceDeployments  
 O modo de ServiceDeployments contém os campos seguintes:  
  
1. **SiteName**  
  
2. **RelativeServicePath**  
  
3. **RelativeApplicationPath**  
  
4. **ServiceName**  
  
5. **ServiceNamespace**  
  
### <a name="the-instancepromotedproperties-view"></a>O modo de InstancePromotedProperties  
 O modo de InstancePromotedProperties contém os seguintes campos. Para obter detalhes sobre as propriedades promovidas, consulte o tópico [Store Extensibility](store-extensibility.md) .  
  
1. **InstanceId**  
  
2. **EncodingOption**  
  
3. **Promocionalname**  
  
4. **Valor #** (um intervalo de campos de **value1** a **Value64**).
