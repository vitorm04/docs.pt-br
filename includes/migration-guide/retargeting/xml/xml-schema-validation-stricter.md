---
ms.openlocfilehash: ef0381dc2ce4373b2a62e8ebefa44152059ca332
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234590"
---
### <a name="xml-schema-validation-is-stricter"></a><span data-ttu-id="377d0-101">A validação do esquema XML está mais rigorosa</span><span class="sxs-lookup"><span data-stu-id="377d0-101">XML schema validation is stricter</span></span>

|   |   |
|---|---|
|<span data-ttu-id="377d0-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="377d0-102">Details</span></span>|<span data-ttu-id="377d0-103">No .NET Framework 4.5, a validação do esquema XML está mais rigorosa.</span><span class="sxs-lookup"><span data-stu-id="377d0-103">In the .NET Framework 4.5, XML schema validation is more strict.</span></span> <span data-ttu-id="377d0-104">Se você usar xsd:anyURI para validar um URI como um protocolo mailto, a validação falhará se houver espaços no URI.</span><span class="sxs-lookup"><span data-stu-id="377d0-104">If you use xsd:anyURI to validate a URI such as a mailto protocol, validation fails if there are spaces in the URI.</span></span> <span data-ttu-id="377d0-105">Nas versões anteriores do .NET Framework, a validação foi bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="377d0-105">In previous versions of the .NET Framework, validation succeeded.</span></span> <span data-ttu-id="377d0-106">A alteração afeta somente aplicativos destinados ao .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="377d0-106">The change affects only applications that target the .NET Framework 4.5.</span></span>|
|<span data-ttu-id="377d0-107">Sugestão</span><span class="sxs-lookup"><span data-stu-id="377d0-107">Suggestion</span></span>|<span data-ttu-id="377d0-108">Se for necessária uma validação menos rigorosa do .NET Framework 4.0, o aplicativo de validação poderá se destinar à versão 4.0 do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="377d0-108">If looser .NET Framework 4.0 validation is needed, the validating application can target version 4.0 of the .NET Framework.</span></span> <span data-ttu-id="377d0-109">No entanto, ao direcionar ao .NET Framework 4.5, é necessário revisar o código para verificar se URIs inválidos (com espaços) não são esperados como valores de atributo com o tipo de dados anyURI.</span><span class="sxs-lookup"><span data-stu-id="377d0-109">When retargeting to .NET Framework 4.5, however, code review should be done to be sure that invalid URIs (with spaces) are not expected as attribute values with the anyURI data type.</span></span>|
|<span data-ttu-id="377d0-110">Escopo</span><span class="sxs-lookup"><span data-stu-id="377d0-110">Scope</span></span>|<span data-ttu-id="377d0-111">Secundário</span><span class="sxs-lookup"><span data-stu-id="377d0-111">Minor</span></span>|
|<span data-ttu-id="377d0-112">Versão</span><span class="sxs-lookup"><span data-stu-id="377d0-112">Version</span></span>|<span data-ttu-id="377d0-113">4.5</span><span class="sxs-lookup"><span data-stu-id="377d0-113">4.5</span></span>|
|<span data-ttu-id="377d0-114">Tipo</span><span class="sxs-lookup"><span data-stu-id="377d0-114">Type</span></span>|<span data-ttu-id="377d0-115">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="377d0-115">Retargeting</span></span>|
