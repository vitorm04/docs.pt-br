---
ms.openlocfilehash: 9c84c9f844a2a7efb9633c11634b069ef6b6033b
ms.sourcegitcommit: 636af37170ae75a11c4f7d1ecd770820e7dfe7bd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2020
ms.locfileid: "91804850"
---
### <a name="datagridview-no-longer-resets-fonts-for-customized-cell-styles"></a><span data-ttu-id="b60c9-101">DataGridView não redefine mais as fontes para estilos de célula personalizados</span><span class="sxs-lookup"><span data-stu-id="b60c9-101">DataGridView no longer resets fonts for customized cell styles</span></span>

<span data-ttu-id="b60c9-102">Quando a fonte de ambiente for alterada, o <xref:System.Windows.Forms.DataGridViewElement.DataGridView> não redefinirá mais as fontes de estilo de célula padrão para corresponder à fonte de ambiente se a fonte de estilo de célula tiver sido personalizada.</span><span class="sxs-lookup"><span data-stu-id="b60c9-102">When the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> no longer resets default cell style fonts to match the ambient font if the cell style font has been customized.</span></span>

#### <a name="change-description"></a><span data-ttu-id="b60c9-103">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="b60c9-103">Change description</span></span>

<span data-ttu-id="b60c9-104">Nas versões anteriores do .NET, se a fonte do ambiente mudar, o <xref:System.Windows.Forms.DataGridViewElement.DataGridView> redefinirá e substituirá as fontes definidas pelo usuário nas <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriedades, e <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> .</span><span class="sxs-lookup"><span data-stu-id="b60c9-104">In previous .NET versions, if the ambient font changes, <xref:System.Windows.Forms.DataGridViewElement.DataGridView> resets and overrides user-defined fonts in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, and <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties.</span></span>

<span data-ttu-id="b60c9-105">A partir do .NET 5,0, se você definir as configurações de fonte nas <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriedades,, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> , essas configurações serão mantidas mesmo quando a fonte do ambiente for alterada.</span><span class="sxs-lookup"><span data-stu-id="b60c9-105">Starting in .NET 5.0, if you configure font settings in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties, those settings are retained even when the ambient font changes.</span></span> <span data-ttu-id="b60c9-106">Para qualquer uma dessas propriedades que você não personalize a fonte, a fonte será alterada para corresponder às configurações de fonte do ambiente.</span><span class="sxs-lookup"><span data-stu-id="b60c9-106">For any of these properties that you don't customize the font, the font will change to match the ambient font settings.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b60c9-107">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="b60c9-107">Reason for change</span></span>

<span data-ttu-id="b60c9-108">Com a [alteração da fonte padrão no .NET Core 3,0](../../../../docs/core/compatibility/winforms.md#default-control-font-changed-to-segoe-ui-9-pt), as configurações de fonte padrão para os vários estilos de célula também foram alteradas.</span><span class="sxs-lookup"><span data-stu-id="b60c9-108">With the [change of the default font in .NET Core 3.0](../../../../docs/core/compatibility/winforms.md#default-control-font-changed-to-segoe-ui-9-pt), the default font settings for the various cell styles also changed.</span></span> <span data-ttu-id="b60c9-109">Esse comportamento não é desejável para aplicativos que dependem de estilo personalizado em seus <xref:System.Windows.Forms.DataGridViewElement.DataGridView> controles e impedia a migração desses aplicativos de .NET Framework para o .net 5,0.</span><span class="sxs-lookup"><span data-stu-id="b60c9-109">This behavior is undesirable for apps that rely on custom styling in their <xref:System.Windows.Forms.DataGridViewElement.DataGridView> controls, and impeded the migration of these apps from .NET Framework to .NET 5.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b60c9-110">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b60c9-110">Version introduced</span></span>

<span data-ttu-id="b60c9-111">.NET 5,0 RC2</span><span class="sxs-lookup"><span data-stu-id="b60c9-111">.NET 5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b60c9-112">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b60c9-112">Recommended action</span></span>

<span data-ttu-id="b60c9-113">Nenhuma ação é necessária em sua parte.</span><span class="sxs-lookup"><span data-stu-id="b60c9-113">No action is required on your part.</span></span> <span data-ttu-id="b60c9-114">No entanto, se você personalizou a fonte <xref:System.Windows.Forms.DataGridView.DefaultCellStyle> nas <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle> Propriedades,, ou <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> e quiser que a fonte corresponda à fonte de ambiente, defina <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> como `null` para cada propriedade.</span><span class="sxs-lookup"><span data-stu-id="b60c9-114">However, if you've customized the font in the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle>, <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle>, or <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle> properties and want the font to match the ambient font, set <xref:System.Windows.Forms.DataGridViewCellStyle.Font?displayProperty=nameWithType> to `null` for each property.</span></span>

#### <a name="category"></a><span data-ttu-id="b60c9-115">Categoria</span><span class="sxs-lookup"><span data-stu-id="b60c9-115">Category</span></span>

- <span data-ttu-id="b60c9-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b60c9-116">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b60c9-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b60c9-117">Affected APIs</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle?displayProperty=fullName>
- <xref:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Windows.Forms.DataGridView.DefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle`
- `P:System.Windows.Forms.DataGridView.RowHeadersDefaultCellStyle`

-->
