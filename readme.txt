
### git-repo 多仓库管理

git-repo [【git-repo @ esrlabs】](https://github.com/esrlabs/git-repo)

几种方法尝试

* default.xml  `fetch="https://github.com/HiltonWei"`
* def.xml      `fetch="git@github.com:HiltonWei"`
* def_git.xml  `fetch="git://github.com:HiltonWei"`

###default.xml
    可以正常执行

### def.xml
    
    repo init -u git@github.com:hiltonwei/manifest -b master -m def.xml

.repo\projects\atree.git\Config文件中的 url是错误的。url = `git@github.com:hiltonwei/git@github.com:HiltonWei/atree )`
    
#### 修复
    
    repo\manifest.py Line:95 _resolveFetchUrl
    
    Line:95 (_resolveFetchUr()） ）

    if manifestUrl.find('git@') != -1: 
      url = url#_print("find git@")
    elif manifestUrl.find(':') != manifestUrl.find('/') - 1:
      url = urllib.parse.urljoin('gopher://' + manifestUrl, url)
      url = re.sub(r'^gopher://', '', url)
    else:
      url = urllib.parse.urljoin(manifestUrl, url)

### def_git.xml
    D:\TestRepo>repo sync

    Fetching project atree
    Fetching project tools
    fatal: Unable to look up github.com:HiltonWei (port 9418) (不知道这样的主机。 )
    fatal: Unable to look up github.com:HiltonWei (port 9418) (不知道这样的主机。 )
    fatal: Unable to look up github.com:HiltonWei (port 9418) (不知道这样的主机。 )
    fatal: Unable to look up github.com:HiltonWei (port 9418) (不知道这样的主机。 )
    
    