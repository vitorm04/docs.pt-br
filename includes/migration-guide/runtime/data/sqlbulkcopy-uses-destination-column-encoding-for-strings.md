---
ms.openlocfilehash: 1329a86db4227f75dfba7c50bbbdc2fc23099528
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619790"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="07ec7-101">SqlBulkCopy usa a codificação de coluna de destino para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="07ec7-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="07ec7-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="07ec7-102">Details</span></span>

<span data-ttu-id="07ec7-103">Quando dados são inseridos em uma coluna, o <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> usa a codificação da coluna de destino em vez da codificação padrão para os tipos <code>VARCHAR</code> e <code>CHAR</code>.</span><span class="sxs-lookup"><span data-stu-id="07ec7-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="07ec7-104">Essa alteração elimina a possibilidade de corrompimento de dados causada pelo uso da codificação padrão quando a coluna de destino não usa a codificação padrão.</span><span class="sxs-lookup"><span data-stu-id="07ec7-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="07ec7-105">Em casos raros, um aplicativo existente pode gerar uma exceção SqlException quando a mudança na codificação produz dados que são grandes demais para caber na coluna de destino.</span><span class="sxs-lookup"><span data-stu-id="07ec7-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="07ec7-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="07ec7-106">Suggestion</span></span>

<span data-ttu-id="07ec7-107">Espere que <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> não corrompa os dados devido a diferenças de codificação.</span><span class="sxs-lookup"><span data-stu-id="07ec7-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="07ec7-108">Se as cadeias de caracteres perto do limite de tamanho da coluna de destino estiverem sendo copiadas, talvez seja necessário codificar previamente os dados (a serem copiados para verificar se os dados serão ajustados na coluna de destino) ou capturar <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span><span class="sxs-lookup"><span data-stu-id="07ec7-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="07ec7-109">Name</span><span class="sxs-lookup"><span data-stu-id="07ec7-109">Name</span></span>    | <span data-ttu-id="07ec7-110">Valor</span><span class="sxs-lookup"><span data-stu-id="07ec7-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="07ec7-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="07ec7-111">Scope</span></span>   |<span data-ttu-id="07ec7-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="07ec7-112">Edge</span></span>|
|<span data-ttu-id="07ec7-113">Versão</span><span class="sxs-lookup"><span data-stu-id="07ec7-113">Version</span></span>|<span data-ttu-id="07ec7-114">4.5</span><span class="sxs-lookup"><span data-stu-id="07ec7-114">4.5</span></span>|
|<span data-ttu-id="07ec7-115">Type</span><span class="sxs-lookup"><span data-stu-id="07ec7-115">Type</span></span>|<span data-ttu-id="07ec7-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="07ec7-116">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="07ec7-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="07ec7-117">Affected APIs</span></span>

-<xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType></li><li><xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)></li></ul>|
