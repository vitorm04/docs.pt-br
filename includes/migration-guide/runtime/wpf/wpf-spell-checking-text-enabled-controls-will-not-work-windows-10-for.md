---
ms.openlocfilehash: 6d7f998cda6326e1f584713576a0aa27b3a68655
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497747"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="83afa-101">Verificação ortográfica do WPF em controles habilitados por texto não funcionará no Windows 10 para idiomas que não estão na lista de idiomas de entrada do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="83afa-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="83afa-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="83afa-102">Details</span></span>

<span data-ttu-id="83afa-103">Ao ser executado no Windows 10, o verificador ortográfico pode não funcionar em controles habilitados por texto do WPF, pois as funcionalidades da plataforma de verificação ortográfica estão disponíveis somente para os idiomas presentes na lista de idiomas de entrada. No Windows 10, quando um idioma é adicionado à lista de teclados disponíveis, o Windows baixa e instala automaticamente um pacote FOD (Recurso sob Demanda) que oferece as funcionalidades de verificação ortográfica.</span><span class="sxs-lookup"><span data-stu-id="83afa-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="83afa-104">Ao adicionar o idioma à lista de idiomas de entrada, o verificador ortográfico terá suporte.</span><span class="sxs-lookup"><span data-stu-id="83afa-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="83afa-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="83afa-105">Suggestion</span></span>

<span data-ttu-id="83afa-106">Lembre-se de que o idioma ou texto a ser verificado ortograficamente precisa ser adicionado como idioma de entrada para a verificação ortográfica funcionar no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="83afa-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="83afa-107">Nome</span><span class="sxs-lookup"><span data-stu-id="83afa-107">Name</span></span>    | <span data-ttu-id="83afa-108">Valor</span><span class="sxs-lookup"><span data-stu-id="83afa-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="83afa-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="83afa-109">Scope</span></span>   |<span data-ttu-id="83afa-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="83afa-110">Edge</span></span>|
|<span data-ttu-id="83afa-111">Versão</span><span class="sxs-lookup"><span data-stu-id="83afa-111">Version</span></span>|<span data-ttu-id="83afa-112">4.6</span><span class="sxs-lookup"><span data-stu-id="83afa-112">4.6</span></span>|
|<span data-ttu-id="83afa-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="83afa-113">Type</span></span>|<span data-ttu-id="83afa-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="83afa-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="83afa-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="83afa-115">Affected APIs</span></span>

<span data-ttu-id="83afa-116">Não detectável via análise de API.</span><span class="sxs-lookup"><span data-stu-id="83afa-116">Not detectable via API analysis.</span></span>

<!--

#### Affected APIs

Not detectable via API analysis.

-->
