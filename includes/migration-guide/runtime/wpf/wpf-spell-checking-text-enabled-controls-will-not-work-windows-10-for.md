---
ms.openlocfilehash: 1d2e4a058008676c6ea85becebd4bb9220569ef3
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621042"
---
### <a name="wpf-spell-checking-in-text-enabled-controls-will-not-work-in-windows-10-for-languages-not-in-the-oss-input-language-list"></a><span data-ttu-id="ff539-101">Verificação ortográfica do WPF em controles habilitados por texto não funcionará no Windows 10 para idiomas que não estão na lista de idiomas de entrada do sistema operacional</span><span class="sxs-lookup"><span data-stu-id="ff539-101">WPF spell checking in text-enabled controls will not work in Windows 10 for languages not in the OS's input language list</span></span>

#### <a name="details"></a><span data-ttu-id="ff539-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="ff539-102">Details</span></span>

<span data-ttu-id="ff539-103">Ao ser executado no Windows 10, o verificador ortográfico pode não funcionar em controles habilitados por texto do WPF, pois as funcionalidades da plataforma de verificação ortográfica estão disponíveis somente para os idiomas presentes na lista de idiomas de entrada. No Windows 10, quando um idioma é adicionado à lista de teclados disponíveis, o Windows baixa e instala automaticamente um pacote FOD (Recurso sob Demanda) que oferece as funcionalidades de verificação ortográfica.</span><span class="sxs-lookup"><span data-stu-id="ff539-103">When running on Windows 10, the spell checker may not work for WPF text-enabled controls because platform spell-checking capabilities are available only for languages present in the input languages list.In Windows 10, when a language is added to the list of available keyboards, Windows automatically downloads and installs a corresponding Feature on Demand (FOD) package that provides spell-checking capabilities.</span></span> <span data-ttu-id="ff539-104">Ao adicionar o idioma à lista de idiomas de entrada, o verificador ortográfico terá suporte.</span><span class="sxs-lookup"><span data-stu-id="ff539-104">By adding the language to the input languages list, the spell checker will be supported.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="ff539-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="ff539-105">Suggestion</span></span>

<span data-ttu-id="ff539-106">Lembre-se de que o idioma ou texto a ser verificado ortograficamente precisa ser adicionado como idioma de entrada para a verificação ortográfica funcionar no Windows 10.</span><span class="sxs-lookup"><span data-stu-id="ff539-106">Be aware that the language or text to be spell-checked must be added as an input language for spell-checking to work in Windows 10.</span></span>

| <span data-ttu-id="ff539-107">Name</span><span class="sxs-lookup"><span data-stu-id="ff539-107">Name</span></span>    | <span data-ttu-id="ff539-108">Valor</span><span class="sxs-lookup"><span data-stu-id="ff539-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="ff539-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="ff539-109">Scope</span></span>   |<span data-ttu-id="ff539-110">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ff539-110">Edge</span></span>|
|<span data-ttu-id="ff539-111">Versão</span><span class="sxs-lookup"><span data-stu-id="ff539-111">Version</span></span>|<span data-ttu-id="ff539-112">4.6</span><span class="sxs-lookup"><span data-stu-id="ff539-112">4.6</span></span>|
|<span data-ttu-id="ff539-113">Type</span><span class="sxs-lookup"><span data-stu-id="ff539-113">Type</span></span>|<span data-ttu-id="ff539-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="ff539-114">Runtime</span></span>|
