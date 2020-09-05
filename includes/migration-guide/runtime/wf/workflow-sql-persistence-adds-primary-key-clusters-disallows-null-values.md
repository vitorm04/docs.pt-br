---
ms.openlocfilehash: cb9305f623044233082286863d2f2d2c7e9d665a
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496869"
---
### <a name="workflow-sql-persistence-adds-primary-key-clusters-and-disallows-null-values-in-some-columns"></a><span data-ttu-id="22afa-101">Persistência do fluxo de trabalho SQL adiciona clusters de chave primária e não permite valores nulos em algumas colunas</span><span class="sxs-lookup"><span data-stu-id="22afa-101">Workflow SQL persistence adds primary key clusters and disallows null values in some columns</span></span>

#### <a name="details"></a><span data-ttu-id="22afa-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="22afa-102">Details</span></span>

<span data-ttu-id="22afa-103">A partir do .NET Framework 4.7, as tabelas criadas para a SWIS (SQL Workflow Instance Store) pelo script SqlWorkflowInstanceStoreSchema.sql usarão chaves primárias em clusters.</span><span class="sxs-lookup"><span data-stu-id="22afa-103">Starting with the .NET Framework 4.7, the tables created for the SQL Workflow Instance Store (SWIS) by the SqlWorkflowInstanceStoreSchema.sql script use clustered primary keys.</span></span> <span data-ttu-id="22afa-104">Por isso, as identidades não são compatíveis com valores <code>null</code>.</span><span class="sxs-lookup"><span data-stu-id="22afa-104">Because of this, identities do not support <code>null</code> values.</span></span> <span data-ttu-id="22afa-105">A operação da SWIS não é afetada por essa alteração.</span><span class="sxs-lookup"><span data-stu-id="22afa-105">The operation of SWIS is not impacted by this change.</span></span> <span data-ttu-id="22afa-106">As atualizações foram feitas serem compatíveis com replicação transacional do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="22afa-106">The updates were made to support SQL Server Transactional Replication.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="22afa-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="22afa-107">Suggestion</span></span>

<span data-ttu-id="22afa-108">O arquivo SQL SqlWorkflowInstanceStoreSchemaUpgrade.sql deve ser aplicado a instalações existentes para usar essa alteração.</span><span class="sxs-lookup"><span data-stu-id="22afa-108">The SQL file SqlWorkflowInstanceStoreSchemaUpgrade.sql must be applied to existing installations in order to experience this change.</span></span> <span data-ttu-id="22afa-109">Novas instalações de banco de dados serão alteradas automaticamente.</span><span class="sxs-lookup"><span data-stu-id="22afa-109">New database installations will automatically have the change.</span></span>

| <span data-ttu-id="22afa-110">Nome</span><span class="sxs-lookup"><span data-stu-id="22afa-110">Name</span></span>    | <span data-ttu-id="22afa-111">Valor</span><span class="sxs-lookup"><span data-stu-id="22afa-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="22afa-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="22afa-112">Scope</span></span>   |<span data-ttu-id="22afa-113">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="22afa-113">Edge</span></span>|
|<span data-ttu-id="22afa-114">Versão</span><span class="sxs-lookup"><span data-stu-id="22afa-114">Version</span></span>|<span data-ttu-id="22afa-115">4.7</span><span class="sxs-lookup"><span data-stu-id="22afa-115">4.7</span></span>|
|<span data-ttu-id="22afa-116">Tipo</span><span class="sxs-lookup"><span data-stu-id="22afa-116">Type</span></span>|<span data-ttu-id="22afa-117">Runtime</span><span class="sxs-lookup"><span data-stu-id="22afa-117">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="22afa-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="22afa-118">Affected APIs</span></span>

<span data-ttu-id="22afa-119">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="22afa-119">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
