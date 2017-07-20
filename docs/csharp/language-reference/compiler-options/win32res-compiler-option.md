---
title: "-win32res (Opções do compilador do C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /win32res
dev_langs:
- CSharp
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 750af9e25369daf17973be0329617ae6505da432
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="win32res-c-compiler-options"></a>/win32res (opções do compilador C#)
A opção **/win32res** insere um recurso do Win32 no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O arquivo de recurso que você deseja adicionar ao seu arquivo de saída.  
  
## <a name="remarks"></a>Comentários  
 Um arquivo de recurso do Win32 pode ser criado com o [Compilador de Recursos](http://go.microsoft.com/fwlink/?LinkId=148370). O Compilador de Recursos é invocado quando você compila um programa do Visual C++; um arquivo .res é criado com base no arquivo .rc.  
  
 Um recurso do Win32 pode conter informações de versão ou de bitmap (ícone) que ajudariam a identificar seu aplicativo no Explorador de Arquivos. Se você não especificar a **/win32res**, o compilador gerará informações de versão com base na versão do assembly.  
  
 Consulte [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (para referenciar) ou [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (para anexar) um arquivo de recursos do .NET Framework.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades do **Aplicativo**.  
  
3.  Clique no botão **Arquivo de Recurso** e escolha um arquivo usando a caixa de combinação.  
  
## <a name="example"></a>Exemplo  
 Compilar `in.cs` e anexar um arquivo de recurso do Win32 `rf.res` para produzir `in.exe`:  
  
```console  
csc /win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
