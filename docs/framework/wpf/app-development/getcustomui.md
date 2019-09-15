---
title: GetCustomUI
ms.date: 03/30/2017
helpviewer_keywords:
- custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
ms.openlocfilehash: a9c4c9d597f5cc1b172213d49a3dd5b8f1c1f671
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991372"
---
# <a name="getcustomui"></a><span data-ttu-id="7f41e-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="7f41e-102">GetCustomUI</span></span>
<span data-ttu-id="7f41e-103">Chamado por PresentationHost.exe para obter mensagens de erro e andamento personalizadas do host, se implementado.</span><span class="sxs-lookup"><span data-stu-id="7f41e-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f41e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f41e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f41e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7f41e-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="7f41e-106">[out] Um ponteiro para o assembly que contém a interface do usuário de andamento fornecida pelo host.</span><span class="sxs-lookup"><span data-stu-id="7f41e-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="7f41e-107">fora O nome da classe que é a interface do usuário de progresso fornecida pelo host, preferivelmente [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] um <xref:System.Windows.Controls.Page> arquivo com é seu elemento de nível superior.</span><span class="sxs-lookup"><span data-stu-id="7f41e-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="7f41e-108">Essa classe reside no assembly especificado por `pwzProgressAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="7f41e-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="7f41e-109">[out] Um ponteiro para o assembly que contém a interface do usuário de erro fornecida pelo host.</span><span class="sxs-lookup"><span data-stu-id="7f41e-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="7f41e-110">fora O nome da classe que é a interface do usuário de erro fornecida pelo host, preferivelmente um arquivo <xref:System.Windows.Controls.Page> XAML com o é seu elemento de nível superior.</span><span class="sxs-lookup"><span data-stu-id="7f41e-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="7f41e-111">Essa classe reside no assembly especificado por `pwzErrorAssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="7f41e-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="7f41e-112">Valor da propriedade/valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7f41e-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="7f41e-113">HRESULT: Ignorado.</span><span class="sxs-lookup"><span data-stu-id="7f41e-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f41e-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f41e-114">Remarks</span></span>  
 <span data-ttu-id="7f41e-115">Um aplicativo host pode ter um tema específico com o qual as interfaces do usuário padrão do PresentationHost.exe podem não estar em conformidade.</span><span class="sxs-lookup"><span data-stu-id="7f41e-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="7f41e-116">Se esse for o caso, o aplicativo host poderá implementar [GetCustomUI](getcustomui.md) para retornar as interfaces do usuário de erro e de andamento para PresentationHost.exe.</span><span class="sxs-lookup"><span data-stu-id="7f41e-116">If this is the case, the host application can implement [GetCustomUI](getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="7f41e-117">PresentationHost.exe sempre chamará [GetCustomUI](getcustomui.md) antes de usar suas interfaces do usuário padrão.</span><span class="sxs-lookup"><span data-stu-id="7f41e-117">PresentationHost.exe will always call [GetCustomUI](getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="7f41e-118">Essa função é chamada uma vez durante a inicialização do PresentationHost.</span><span class="sxs-lookup"><span data-stu-id="7f41e-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f41e-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f41e-119">See also</span></span>

- [<span data-ttu-id="7f41e-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="7f41e-120">IWpfHostSupport</span></span>](iwpfhostsupport.md)
