---
ms.openlocfilehash: 3b7309347c643d89a28331c6ef3cac36085a969a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234084"
---
### <a name="wpf-windows-are-rendered-without-clipping-when-extending-outside-a-single-monitor"></a><span data-ttu-id="26f58-101">Janelas do WPF são renderizadas sem distorção ao se estender para fora de um único monitor</span><span class="sxs-lookup"><span data-stu-id="26f58-101">WPF windows are rendered without clipping when extending outside a single monitor</span></span>

|   |   |
|---|---|
|<span data-ttu-id="26f58-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="26f58-102">Details</span></span>|<span data-ttu-id="26f58-103">No .NET Framework 4.6 em execução no Windows 8 e superior, a janela inteira é renderizada sem distorção quando ela se estende para fora da exibição única em um cenário de vários monitores.</span><span class="sxs-lookup"><span data-stu-id="26f58-103">In the .NET Framework 4.6 running on Windows 8 and above, the entire window is rendered without clipping when it extends outside of single display in a multi-monitor scenario.</span></span> <span data-ttu-id="26f58-104">Isso é diferente de versões anteriores do .NET Framework, que distorceriam janelas do WPF que se estendiam para fora de uma única exibição.</span><span class="sxs-lookup"><span data-stu-id="26f58-104">This is different from previous versions of the .NET Framework which would clip WPF windows that extended beyond a single display.</span></span>|
|<span data-ttu-id="26f58-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="26f58-105">Suggestion</span></span>|<span data-ttu-id="26f58-106">Esse comportamento (com distorção ou não) pode ser definido explicitamente usando o elemento <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> em <code>&lt;appSettings&gt;</code> no arquivo de configuração do aplicativo ou definindo a propriedade <code>EnableMultiMonitorDisplayClipping</code> durante a inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="26f58-106">This behavior (whether to clip or not) can be explicitly set using the <code>&lt;EnableMultiMonitorDisplayClipping&gt;</code> element in <code>&lt;appSettings&gt;</code> in an application's configuration file, or by setting the <code>EnableMultiMonitorDisplayClipping</code> property at app startup.</span></span>|
|<span data-ttu-id="26f58-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="26f58-107">Scope</span></span>|<span data-ttu-id="26f58-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="26f58-108">Minor</span></span>|
|<span data-ttu-id="26f58-109">Versão</span><span class="sxs-lookup"><span data-stu-id="26f58-109">Version</span></span>|<span data-ttu-id="26f58-110">4.6</span><span class="sxs-lookup"><span data-stu-id="26f58-110">4.6</span></span>|
|<span data-ttu-id="26f58-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="26f58-111">Type</span></span>|<span data-ttu-id="26f58-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="26f58-112">Runtime</span></span>|
