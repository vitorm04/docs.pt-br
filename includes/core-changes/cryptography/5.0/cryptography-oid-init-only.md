---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557992"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="14aec-101">System. Security. Cryptography. OID é funcionalmente somente init</span><span class="sxs-lookup"><span data-stu-id="14aec-101">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="14aec-102">A <xref:System.Security.Cryptography.Oid?displayProperty=fullName> classe, que é usada para representar valores de identificador de objeto ASN. 1 e seus nomes "amigáveis", anteriormente era totalmente mutável.</span><span class="sxs-lookup"><span data-stu-id="14aec-102">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="14aec-103">Essa imutabilidade costuma ser despercebida ou surgiu como uma surpresa.</span><span class="sxs-lookup"><span data-stu-id="14aec-103">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="14aec-104">Os setters de propriedade agora lançam um <xref:System.PlatformNotSupportedException> quando você tenta alterar o valor depois que ele já foi atribuído.</span><span class="sxs-lookup"><span data-stu-id="14aec-104">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

#### <a name="change-description"></a><span data-ttu-id="14aec-105">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="14aec-105">Change description</span></span>

<span data-ttu-id="14aec-106">Em versões anteriores, os setters de propriedade em <xref:System.Security.Cryptography.Oid> podem ser usados para alterar o valor das <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> Propriedades e.</span><span class="sxs-lookup"><span data-stu-id="14aec-106">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="14aec-107">No .NET 5,0 e versões posteriores, os setters de propriedade só podem ser usados para inicializar o valor.</span><span class="sxs-lookup"><span data-stu-id="14aec-107">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="14aec-108">Depois que a propriedade tiver um valor, de um construtor ou de uma chamada anterior para o setter de propriedade, o setter da propriedade sempre lançará um <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="14aec-108">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="14aec-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="14aec-109">Reason for change</span></span>

<span data-ttu-id="14aec-110">Essa alteração permite a reutilização de <xref:System.Security.Cryptography.Oid> objetos como parte dos valores de retorno em APIs públicas para reduzir os perfis de alocação de objetos.</span><span class="sxs-lookup"><span data-stu-id="14aec-110">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="14aec-111">Ele evita a necessidade de criar cópias "defensivas" temporárias quando <xref:System.Security.Cryptography.Oid> os valores são usados como entradas.</span><span class="sxs-lookup"><span data-stu-id="14aec-111">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="14aec-112">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="14aec-112">Version introduced</span></span>

<span data-ttu-id="14aec-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="14aec-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="14aec-114">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="14aec-114">Recommended action</span></span>

<span data-ttu-id="14aec-115">Evite usar os <xref:System.Security.Cryptography.Oid> setters de propriedade diferentes de para a inicialização do objeto.</span><span class="sxs-lookup"><span data-stu-id="14aec-115">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="14aec-116">Para representar um novo valor, use uma nova instância em vez de alterar o valor em um objeto existente.</span><span class="sxs-lookup"><span data-stu-id="14aec-116">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

#### <a name="category"></a><span data-ttu-id="14aec-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="14aec-117">Category</span></span>

<span data-ttu-id="14aec-118">Criptografia</span><span class="sxs-lookup"><span data-stu-id="14aec-118">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14aec-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="14aec-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
