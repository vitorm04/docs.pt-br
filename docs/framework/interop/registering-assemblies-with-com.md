---
title: Registrando assemblies com o COM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1473fa07b57dcd19ea192db6cdb0a395f119b159
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="registering-assemblies-with-com"></a>Registrando assemblies com o COM
Você pode executar uma ferramenta de linha de comando chamada [Ferramenta de registro do Assembly (Regasm.exe)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md) para registrar ou cancelar o registro de um assembly para uso com o COM. Regasm.exe adiciona informações sobre a classe no registro do sistema para que clientes COM possam usar a classe do .NET Framework de forma transparente. A classe <xref:System.Runtime.InteropServices.RegistrationServices> fornece a funcionalidade equivalente.  
  
 Um componente gerenciado deve ser registrado no registro do Windows antes que ele possa ser ativado de um cliente COM. A tabela a seguir mostra as chaves que normalmente adicionam o Regasm.exe ao Registro do Windows. (000000 indica o valor real do GUID.)  
  
|GUID|Descrição|Chave do Registro|  
|----------|-----------------|------------------|  
|CLSID|Identificador de classe|HKEY_CLASSES_ROOT\CLSID\\{000…000}|  
|IID|Identificador de interface|HKEY_CLASSES_ROOT\Interface\\{000…000}|  
|LIBID|Identificador de biblioteca|HKEY_CLASSES_ROOT\TypeLib\\{000…000}|  
|ProgID|Identificador programático|HKEY_CLASSES_ROOT\000…000|  
  
 Sob a chave HKCR\CLSID\\{0000... 0000}, o valor padrão é definido como o ProgID da classe e dois novos valores nomeados, Class e Assembly, são adicionados. O tempo de execução lê o valor de Assembly do registro e a passa para o resolvedor de assembly de tempo de execução. O resolvedor de assembly tenta localizar o assembly, com base em informações de assembly como o número de versão e o nome. Para ser localizado por um resolvedor de assembly, o assembly deve estar em um dos seguintes locais:  
  
-   O cache de assembly global (deve ser um assembly de nome forte).  
  
-   No diretório do aplicativo. Assemblies carregados no caminho do aplicativo só são acessíveis por meio desse aplicativo.  
  
-   Ao longo de um caminho de arquivo especificado com a opção **/codebase** para Regasm.exe.  
  
 Regasm.exe também cria a chave InProcServer32 sob a chave HKCR\CLSID\\{0000... 0000}. O valor padrão para a chave é definido como o nome da DLL que inicializa o Common Language Runtime (Mscoree.dll).  
  
## <a name="examining-registry-entries"></a>Examinando Entradas do Registro  
 A interoperabilidade COM fornece uma implementação de fábrica de classes padrão para criar uma instância de qualquer classe do .NET Framework. Os clientes poderão chamar **DllGetClassObject** na DLL gerenciada para obter uma fábrica de classes e criar objetos, assim como fariam com qualquer outro componente COM.  
  
 Para a subchave `InprocServer32`, uma referência a Mscoree.dll é exibida no lugar de uma biblioteca de tipos COM tradicional para indicar que o Common Language Runtime cria o objeto gerenciado.  
  
## <a name="see-also"></a>Consulte também  
 [Expondo componentes do .NET Framework ao COM](../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Como referenciar tipos do .NET com base no COM](../../../docs/framework/interop/how-to-reference-net-types-from-com.md)  
 [Chamar um objeto .NET](http://msdn.microsoft.com/en-us/40c9626c-aea6-4bad-b8f0-c1de462efd33)  
 [Implantando um aplicativo para acesso COM](http://msdn.microsoft.com/en-us/fb63564c-c1b9-4655-a094-a235625882ce)
