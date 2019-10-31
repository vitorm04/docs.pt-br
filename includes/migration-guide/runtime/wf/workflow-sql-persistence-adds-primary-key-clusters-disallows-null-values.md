---
ms.openlocfilehash: 9e98d3bca645cf82bf4fe99160dd096b0e274ef7
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67802448"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="e8d36-101">Persistência do fluxo de trabalho SQL adiciona clusters de chave primária e não permite valores nulos em algumas colunas</span><span class="sxs-lookup"><span data-stu-id="e8d36-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

|   |   |
|---|---|
|<span data-ttu-id="e8d36-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="e8d36-102">Details</span></span>|<span data-ttu-id="e8d36-103">A partir do .NET Framework 4.7, as tabelas criadas para a SWIS (SQL Workflow Instance Store) pelo script SqlWorkflowInstanceStoreSchema.sql usarão chaves primárias em clusters.</span><span class="sxs-lookup"><span data-stu-id="e8d36-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="e8d36-104">Por isso, as identidades não são compatíveis com valores <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="e8d36-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="e8d36-105">A operação da SWIS não é afetada por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="e8d36-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="e8d36-106">As atualizações foram feitas serem compatíveis com replicação transacional do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="e8d36-106">The updates were made to support SQL Server Transactional Replication.</span></span>|
|<span data-ttu-id="e8d36-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="e8d36-107">Suggestion</span></span>|<span data-ttu-id="e8d36-108">O arquivo SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql deve ser aplicado a instalações existentes para usar essa alteração.</span><span class="sxs-lookup"><span data-stu-id="e8d36-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="e8d36-109">Novas instalações de banco de dados serão alteradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="e8d36-109">New database installations will automatically have the change.</span></span>|
|<span data-ttu-id="e8d36-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="e8d36-110">Scope</span></span>|<span data-ttu-id="e8d36-111">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="e8d36-111">Edge</span></span>|
|<span data-ttu-id="e8d36-112">Versão</span><span class="sxs-lookup"><span data-stu-id="e8d36-112">Version</span></span>|<span data-ttu-id="e8d36-113">4.7</span><span class="sxs-lookup"><span data-stu-id="e8d36-113">4.7</span></span>|
|<span data-ttu-id="e8d36-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="e8d36-114">Type</span></span>|<span data-ttu-id="e8d36-115">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e8d36-115">Runtime</span></span>|

