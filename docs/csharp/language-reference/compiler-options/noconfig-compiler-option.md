---
title: -noconfig (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: b689a4bf0d8a1e57bf36f8ded7f2c9308f241670
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43402688"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (opções do compilador C#)
A opção **-noconfig** informa que o compilador não deve compilar com o arquivo csc.rsp, localizado no mesmo diretório que o arquivo csc.exe e carregado dele.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>Comentários  
 O arquivo csc.rsp referencia todos os assemblies que acompanham o .NET Framework. As referências reais que o ambiente de desenvolvimento do Visual Studio .NET inclui dependem do tipo de projeto.  
  
 É possível modificar o arquivo csc.rsp e especificar opções do compilador adicionais que devem ser incluídas em cada compilação na linha de comando com csc.exe (exceto a opção **-noconfig**).  
  
 O compilador processa as opções passadas para o comando **csc** pela última vez. Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo csc.rsp.  
  
 Se você não desejar que o compilador procure e use as configurações no arquivo csc.rsp, especifique **-noconfig**.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="see-also"></a>Consulte também  

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
