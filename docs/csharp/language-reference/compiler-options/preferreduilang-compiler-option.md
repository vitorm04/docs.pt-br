---
title: -preferreduilang (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 7ebafcf446c9033c93e0c5fa5e11ea2930bd2e1e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602564"
---
# <a name="-preferreduilang-c-compiler-options"></a><span data-ttu-id="7f2c7-102">-preferreduilang (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="7f2c7-102">-preferreduilang (C# Compiler Options)</span></span>
<span data-ttu-id="7f2c7-103">Usando a opção do compilador `-preferreduilang`, é possível especificar o idioma em que o compilador C# exibe a saída, como mensagens de erro.</span><span class="sxs-lookup"><span data-stu-id="7f2c7-103">By using the `-preferreduilang` compiler option, you can specify the language in which the C# compiler displays output, such as error messages.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f2c7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7f2c7-104">Syntax</span></span>  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a><span data-ttu-id="7f2c7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7f2c7-105">Arguments</span></span>  
 `language`  
 <span data-ttu-id="7f2c7-106">O [nome do idioma](/windows/desktop/Intl/language-names) do idioma a ser usado para a saída do compilador.</span><span class="sxs-lookup"><span data-stu-id="7f2c7-106">The [language name](/windows/desktop/Intl/language-names) of the language to use for compiler output.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f2c7-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7f2c7-107">Remarks</span></span>  
 <span data-ttu-id="7f2c7-108">É possível usar a opção do compilador `-preferreduilang` para especificar o idioma que você deseja que o compilador C# use para mensagens de erro e outras saídas de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="7f2c7-108">You can use the `-preferreduilang` compiler option to specify the language that you want the C# compiler to use for error messages and other command-line output.</span></span> <span data-ttu-id="7f2c7-109">Se o pacote de idiomas do idioma não estiver instalado, a configuração de idioma do sistema operacional será usada e nenhum erro será relatado.</span><span class="sxs-lookup"><span data-stu-id="7f2c7-109">If the language pack for the language is not installed, the language setting of the operating system is used instead, and no error is reported.</span></span>  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a><span data-ttu-id="7f2c7-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7f2c7-110">Requirements</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f2c7-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7f2c7-111">See also</span></span>

- [<span data-ttu-id="7f2c7-112">Opções do compilador de C#</span><span class="sxs-lookup"><span data-stu-id="7f2c7-112">C# Compiler Options</span></span>](./index.md)
