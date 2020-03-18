---
title: 'Como: Conjuntos de carga e descarga'
ms.date: 08/19/2019
ms.assetid: 6a4f490f-3576-471f-9533-003737cad4a3
ms.openlocfilehash: a520ffd41c3465737be7494d374cbcf64e3f1b85
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "78155770"
---
# <a name="how-to-load-and-unload-assemblies"></a>Como: Conjuntos de carga e descarga
Os conjuntos referenciados pelo seu programa serão automaticamente carregados pelo tempo de execução do idioma comum, mas também é possível carregar dinamicamente conjuntos específicos no domínio atual do aplicativo. Para obter mais informações, [consulte Como: Carregar conjuntos em um domínio de aplicativo](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md).

No Quadro .NET, não há como descarregar um conjunto individual sem descarregar todos os domínios de aplicativos que o contêm. Mesmo se o assembly sair do escopo, o arquivo do assembly real permanecerá carregado até que todos os domínios do aplicativo que o contenham sejam descarregados. No .NET Core, a <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> classe lida com o descarregamento de montagens. Para obter mais informações, consulte [Como usar e depurar a capacidade de descarga do conjunto no .NET Core](unloadability.md).

## <a name="load-and-unload-assemblies"></a>carregar ou descarregar assemblies

Para carregar um conjunto em um domínio de aplicativo, use <xref:System.AppDomain> um <xref:System.Reflection.Assembly>dos vários métodos de carga contidos nas classes e . Para obter mais informações, [consulte Como: Carregar conjuntos em um domínio de aplicativo](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md). Observe que o .NET Core suporta apenas um único domínio de aplicativo.

Para descarregar um conjunto no Quadro .NET, você deve descarregar todos os domínios do aplicativo que o contêm. Para descarregar um domínio <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> de aplicativo, use o método. Para obter mais informações, [consulte Como: Descarregar um domínio de aplicativo](../../framework/app-domains/how-to-unload-an-application-domain.md).

Se você quiser descarregar alguns conjuntos, mas não outros em um aplicativo .NET Framework, considere criar um novo domínio de aplicativo, executar o código dentro desse domínio e, em seguida, descarregar esse domínio do aplicativo. Para obter mais informações, [consulte Como: Descarregar um domínio de aplicativo](../../framework/app-domains/how-to-unload-an-application-domain.md).  

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../../csharp/programming-guide/index.md)
- [Conceitos de programação (Visual Basic)](../../visual-basic/programming-guide/concepts/index.md)
- [Assemblies no .NET](index.md)
- [Como: Carregar conjuntos em um domínio de aplicativo](../../framework/app-domains/how-to-load-assemblies-into-an-application-domain.md)
