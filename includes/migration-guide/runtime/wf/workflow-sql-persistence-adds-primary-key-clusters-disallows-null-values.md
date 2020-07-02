---
ms.openlocfilehash: 809ca85b347fabc44573e2e0c5a43261d68590d3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621023"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="a8858-101">Persistência do fluxo de trabalho SQL adiciona clusters de chave primária e não permite valores nulos em algumas colunas</span><span class="sxs-lookup"><span data-stu-id="a8858-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="a8858-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="a8858-102">Details</span></span>

<span data-ttu-id="a8858-103">A partir do .NET Framework 4.7, as tabelas criadas para a SWIS (SQL Workflow Instance Store) pelo script SqlWorkflowInstanceStoreSchema.sql usarão chaves primárias em clusters.</span><span class="sxs-lookup"><span data-stu-id="a8858-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="a8858-104">Por isso, as identidades não são compatíveis com valores <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="a8858-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="a8858-105">A operação da SWIS não é afetada por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="a8858-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="a8858-106">As atualizações foram feitas serem compatíveis com replicação transacional do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a8858-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="a8858-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="a8858-107">Suggestion</span></span>

<span data-ttu-id="a8858-108">O arquivo SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql deve ser aplicado a instalações existentes para usar essa alteração.</span><span class="sxs-lookup"><span data-stu-id="a8858-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="a8858-109">Novas instalações de banco de dados serão alteradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="a8858-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="a8858-110">Name</span><span class="sxs-lookup"><span data-stu-id="a8858-110">Name</span></span>    | <span data-ttu-id="a8858-111">Valor</span><span class="sxs-lookup"><span data-stu-id="a8858-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="a8858-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="a8858-112">Scope</span></span>   |<span data-ttu-id="a8858-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a8858-113">Edge</span></span>|
|<span data-ttu-id="a8858-114">Versão</span><span class="sxs-lookup"><span data-stu-id="a8858-114">Version</span></span>|<span data-ttu-id="a8858-115">4.7</span><span class="sxs-lookup"><span data-stu-id="a8858-115">4.7</span></span>|
|<span data-ttu-id="a8858-116">Type</span><span class="sxs-lookup"><span data-stu-id="a8858-116">Type</span></span>|<span data-ttu-id="a8858-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="a8858-117">Runtime</span></span>|
