---
ms.openlocfilehash: fd9f4f3de8f7be39242d4ff6924d480f20a1a06b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496498"
---
### <a name="sqlbulkcopy-uses-destination-column-encoding-for-strings"></a><span data-ttu-id="b0a3c-101">SqlBulkCopy usa a codificação de coluna de destino para cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="b0a3c-101">SqlBulkCopy uses destination column encoding for strings</span></span>

#### <a name="details"></a><span data-ttu-id="b0a3c-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="b0a3c-102">Details</span></span>

<span data-ttu-id="b0a3c-103">Quando dados são inseridos em uma coluna, o <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> usa a codificação da coluna de destino em vez da codificação padrão para os tipos <code>VARCHAR</code> e <code>CHAR</code>.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-103">When inserting data into a column, <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> uses the encoding of the destination column rather than the default encoding for <code>VARCHAR</code> and <code>CHAR</code> types.</span></span> <span data-ttu-id="b0a3c-104">Essa alteração elimina a possibilidade de corrompimento de dados causada pelo uso da codificação padrão quando a coluna de destino não usa a codificação padrão.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-104">This change eliminates the possibility of data corruption caused by using the default encoding when the destination column does not use the default encoding.</span></span> <span data-ttu-id="b0a3c-105">Em casos raros, um aplicativo existente pode gerar uma exceção SqlException quando a mudança na codificação produz dados que são grandes demais para caber na coluna de destino.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-105">In rare cases, an existing application may throw a SqlException exception if the change in encoding produces data that is too big to fit into the destination column.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b0a3c-106">Sugestão</span><span class="sxs-lookup"><span data-stu-id="b0a3c-106">Suggestion</span></span>

<span data-ttu-id="b0a3c-107">Espere que <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> não corrompa os dados devido a diferenças de codificação.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-107">Expect that <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=fullName> will no longer corrupt data due to encoding differences.</span></span> <span data-ttu-id="b0a3c-108">Se as cadeias de caracteres perto do limite de tamanho da coluna de destino estiverem sendo copiadas, talvez seja necessário codificar previamente os dados (a serem copiados para verificar se os dados serão ajustados na coluna de destino) ou capturar <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span><span class="sxs-lookup"><span data-stu-id="b0a3c-108">If strings near the destination column's size limit are being copied, it may be necessary to either pre-encode data (to be copied to check that the data will fit in the destination column) or catch <xref:System.Data.SqlClient.SqlException?displayProperty=fullName>s.</span></span>

| <span data-ttu-id="b0a3c-109">Nome</span><span class="sxs-lookup"><span data-stu-id="b0a3c-109">Name</span></span>    | <span data-ttu-id="b0a3c-110">Valor</span><span class="sxs-lookup"><span data-stu-id="b0a3c-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b0a3c-111">Escopo</span><span class="sxs-lookup"><span data-stu-id="b0a3c-111">Scope</span></span>   |<span data-ttu-id="b0a3c-112">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="b0a3c-112">Edge</span></span>|
|<span data-ttu-id="b0a3c-113">Versão</span><span class="sxs-lookup"><span data-stu-id="b0a3c-113">Version</span></span>|<span data-ttu-id="b0a3c-114">4.5</span><span class="sxs-lookup"><span data-stu-id="b0a3c-114">4.5</span></span>|
|<span data-ttu-id="b0a3c-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="b0a3c-115">Type</span></span>|<span data-ttu-id="b0a3c-116">Runtime</span><span class="sxs-lookup"><span data-stu-id="b0a3c-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="b0a3c-117">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b0a3c-117">Affected APIs</span></span>

- <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType>
- <xref:System.Data.SqlClient.SqlBulkCopy.%23ctor(System.Data.SqlClient.SqlConnection)>

<!--

#### Affected APIs

- `T:System.Data.SqlClient.SqlBulkCopy`
- `M:System.Data.SqlClient.SqlBulkCopy.#ctor(System.Data.SqlClient.SqlConnection)`

-->
