---
title: "-pdb (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /pdb
dev_langs:
- CSharp
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: 8
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 7c72c12347a9096aeed063b84310356cb07b49c3
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="pdb-c-compiler-options"></a>/pdb (C# 編譯器選項)
**/pdb** 編譯器選項指定偵錯符號檔的名稱和位置。  
  
## <a name="syntax"></a>語法  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a>引數  
 `filename`  
 偵錯符號檔案的名稱和位置。  
  
## <a name="remarks"></a>備註  
 當您指定 [/debug (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md) 時，編譯器會在相同的目錄中建立 .pdb 檔案，而編譯器會在此目錄中建立檔案名稱與輸出檔案名稱相同的輸出檔案 (.exe 或 .dll)。  
  
 **/pdb** 可讓您指定 .pdb 檔案的非預設檔案名稱和位置。  
  
 無法在 Visual Studio 開發環境中設定此編譯器選項，也無法以程式設計方式進行變更。  
  
## <a name="example"></a>範例  
 編譯 `t.cs` 並建立稱為 tt.pdb 的 .pdb 檔案：  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a>另請參閱  
 [C# 編譯器選項](../../../csharp/language-reference/compiler-options/index.md)   
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)

