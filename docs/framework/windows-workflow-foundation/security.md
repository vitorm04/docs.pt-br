---
title: Segurança
ms.date: 03/30/2017
ms.assetid: 737ec121-bfc5-4b75-a504-2d53c2c8af39
ms.openlocfilehash: b8fd870bcd14b8a80861914448f75fafe6af2863
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="security"></a>Segurança
A instância Store de fluxo de trabalho do SQL usa as seguintes funções de segurança de base de dados para proteger o acesso a informações do estado da instância na base de dados de persistência.  
  
-   **System.Activities.DurableInstancing.InstanceStoreUsers**. Essa função tem acesso de leitura e gravação para a exibição e a direita públicas de execução procedimentos armazenados que estão envolvidos na criação, em carregar e salvar em instâncias.  
  
-   **System.Activities.DurableInstancing.InstanceStoreObservers**. Essa função tem acesso somente leitura modos de exibição públicas.  
  
-   **System.Activities.DurableInstancing.WorkflowActivationUsers**. Essa função tem direitos de execução procedimentos armazenados que estão envolvidos no processo de ativação da instância. Para obter mais informações sobre a ativação de instância, consulte [ativação de instância](../../../docs/framework/windows-workflow-foundation/instance-activation.md). A conta de usuário em que um host genérico (como o serviço de gerenciamento de fluxo de trabalho [!INCLUDE[dublin](../../../includes/dublin-md.md)]) executa deve ser adicionada à essa função de base de dados.  
  
 Para obter mais informações sobre a segurança de armazenamentos de persistência com a malha de aplicativos do Windows Server, consulte [configuração de segurança para os armazenamentos de persistência na malha de aplicativos](http://go.microsoft.com/fwlink/?LinkId=201208)  
  
> [!CAUTION]
>  Um cliente que tenha acesso a seus próprios dados de instância no armazenamento de instância tem acesso a todas as outras instâncias no mesmo armazenamento de instância. O armazenamento de instância não suporta especificar permissões de segurança no nível da instância. Você deve criar armazenamentos separados de instância e mapear grupos/usuários diferentes para ter acesso aos armazenamentos diferentes.
