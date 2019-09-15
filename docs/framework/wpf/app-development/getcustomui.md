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
# <a name="getcustomui"></a>GetCustomUI
Chamado por PresentationHost.exe para obter mensagens de erro e andamento personalizadas do host, se implementado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pwzProgressAssemblyName`  
  
 [out] Um ponteiro para o assembly que contém a interface do usuário de andamento fornecida pelo host.  
  
 `pwzProgressClassName`  
  
 fora O nome da classe que é a interface do usuário de progresso fornecida pelo host, preferivelmente [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] um <xref:System.Windows.Controls.Page> arquivo com é seu elemento de nível superior. Essa classe reside no assembly especificado por `pwzProgressAssemblyName`.  
  
 `pwzErrorAssemblyName`  
  
 [out] Um ponteiro para o assembly que contém a interface do usuário de erro fornecida pelo host.  
  
 `pwzErrorClassName`  
  
 fora O nome da classe que é a interface do usuário de erro fornecida pelo host, preferivelmente um arquivo <xref:System.Windows.Controls.Page> XAML com o é seu elemento de nível superior. Essa classe reside no assembly especificado por `pwzErrorAssemblyName`.  
  
## <a name="property-valuereturn-value"></a>Valor da propriedade/valor de retorno  
 HRESULT: Ignorado.  
  
## <a name="remarks"></a>Comentários  
 Um aplicativo host pode ter um tema específico com o qual as interfaces do usuário padrão do PresentationHost.exe podem não estar em conformidade. Se esse for o caso, o aplicativo host poderá implementar [GetCustomUI](getcustomui.md) para retornar as interfaces do usuário de erro e de andamento para PresentationHost.exe. PresentationHost.exe sempre chamará [GetCustomUI](getcustomui.md) antes de usar suas interfaces do usuário padrão.  
  
 Essa função é chamada uma vez durante a inicialização do PresentationHost.  
  
## <a name="see-also"></a>Consulte também

- [IWpfHostSupport](iwpfhostsupport.md)
