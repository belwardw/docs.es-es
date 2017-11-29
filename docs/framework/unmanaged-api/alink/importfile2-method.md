---
title: "ImportFile2 (Método)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.ImportFile2
api_location: alink.dll
api_type: COM
f1_keywords: ImportFile2
helpviewer_keywords: ImportFile2 method
ms.assetid: 9a6be861-c260-4a35-acea-3372ea515a0f
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4d7e842152e84992124ec29cd551c3b5d50a6d61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2017
---
# <a name="importfile2-method"></a><span data-ttu-id="dedcf-102">ImportFile2 (Método)</span><span class="sxs-lookup"><span data-stu-id="dedcf-102">ImportFile2 Method</span></span>
<span data-ttu-id="dedcf-103">Importa ensamblados y módulos no enlazados.</span><span class="sxs-lookup"><span data-stu-id="dedcf-103">Imports assemblies and unbound modules.</span></span> <span data-ttu-id="dedcf-104">Este método es similar a [ImportFile (método)](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), pero funciona incluso si el archivo que se va a importar no existe en el disco.</span><span class="sxs-lookup"><span data-stu-id="dedcf-104">This method is like [ImportFile Method](../../../../docs/framework/unmanaged-api/alink/importfile-method.md), but works even if the file being imported does not exist on disk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dedcf-105">Sintaxis</span><span class="sxs-lookup"><span data-stu-id="dedcf-105">Syntax</span></span>  
  
```  
HRESULT ImportFile2(  
    LPCWSTR         pszFilename,  
    LPCWSTR         pszTargetName,  
    IMetaDataAssemblyImport* pAssemblyScopeIn,  
    BOOL            fSmartImport,  
    mdToken*        pImportToken,  
    IMetaDataAssemblyImport** ppAssemblyScope,  
    DWORD*          pdwCountOfScopes  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dedcf-106">Parámetros</span><span class="sxs-lookup"><span data-stu-id="dedcf-106">Parameters</span></span>  
 `pszFilename`  
 <span data-ttu-id="dedcf-107">Nombre del archivo que desea importar.</span><span class="sxs-lookup"><span data-stu-id="dedcf-107">Name of file to be imported.</span></span>  
  
 `pszTargetName`  
 <span data-ttu-id="dedcf-108">Nombre de archivo de salida opcionales que puede usarse para cambiar el nombre del archivo cuando se vincule al ensamblado.</span><span class="sxs-lookup"><span data-stu-id="dedcf-108">Optional output file name that can be used to rename the file as it is linked into the assembly.</span></span>  
  
 `pAssemblyScopeIn`  
 <span data-ttu-id="dedcf-109">Ámbito opcional [IMetaDataAssemblyImport (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfaz.</span><span class="sxs-lookup"><span data-stu-id="dedcf-109">Optional scope [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span>  
  
 `fSmartImport`  
 <span data-ttu-id="dedcf-110">Si es TRUE, se utiliza ImportTypes, en caso contrario, la importación debe realizarse manualmente.</span><span class="sxs-lookup"><span data-stu-id="dedcf-110">If TRUE, ImportTypes is used, otherwise importing must be performed manually.</span></span>  
  
 `pImportToken`  
 <span data-ttu-id="dedcf-111">Recibe el identificador para el archivo o ensamblado.</span><span class="sxs-lookup"><span data-stu-id="dedcf-111">Receives the ID for the file or assembly.</span></span>  
  
 `ppAssemblyScope`  
 <span data-ttu-id="dedcf-112">Recibe la [IMetaDataAssemblyImport (interfaz)](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interfaz.</span><span class="sxs-lookup"><span data-stu-id="dedcf-112">Receives the [IMetaDataAssemblyImport Interface](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md) interface.</span></span> <span data-ttu-id="dedcf-113">Es NULL si el archivo no es un ensamblado.</span><span class="sxs-lookup"><span data-stu-id="dedcf-113">NULL if the file is not an assembly.</span></span>  
  
 `pdwCountOfScopes`  
 <span data-ttu-id="dedcf-114">Recibe el número de archivos y/o ámbitos importados.</span><span class="sxs-lookup"><span data-stu-id="dedcf-114">Receives the found of files and/or scopes imported.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dedcf-115">Valor devuelto</span><span class="sxs-lookup"><span data-stu-id="dedcf-115">Return Value</span></span>  
 <span data-ttu-id="dedcf-116">Devuelve S_OK si el método tiene éxito.</span><span class="sxs-lookup"><span data-stu-id="dedcf-116">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dedcf-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="dedcf-117">Requirements</span></span>  
 <span data-ttu-id="dedcf-118">Requiere alink.h.</span><span class="sxs-lookup"><span data-stu-id="dedcf-118">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dedcf-119">Vea también</span><span class="sxs-lookup"><span data-stu-id="dedcf-119">See Also</span></span>  
 [<span data-ttu-id="dedcf-120">IALink (interfaz)</span><span class="sxs-lookup"><span data-stu-id="dedcf-120">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="dedcf-121">IALink2 (interfaz)</span><span class="sxs-lookup"><span data-stu-id="dedcf-121">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="dedcf-122">API de ALink</span><span class="sxs-lookup"><span data-stu-id="dedcf-122">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)