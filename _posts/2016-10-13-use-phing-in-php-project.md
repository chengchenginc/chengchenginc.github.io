---
layout:     post
title:      "PHP project使用phing工具"
date:       2016-10-13 12:00:00
tags: [php,phing]
categories: [developer]
---
<h5>1、使用phing create a sample target</h5>

	<target name="echo">
		<echo msg="welcome, hello！ ">
	</target>

cmd执行 ```phing echo```


<h5>2、使用phing deploy FTP</h5>


	<fileset dir="." id="allfiles">
        <include name="**" />
    </fileset>

    <target name="deploy">
     	<phingcall target="compile" />
        <echo msg="start deploy:${ftp.host}"/>
        <ftpdeploy
                host="${ftp.host}"
                port="${ftp.port}"
                username="${ftp.username}"
                password="${ftp.password}"
				passive = "true"
                dir="${ftp.dir}"
				depends="true" skiponsamesize="true">
          <fileset refid="appfiles" />
        </ftpdeploy>
        <echo msg="finish deploy"/>
    </target>

cmd执行 ```phing deploy```

<h5>3、使用phing manage your project's config </h5>

	<target name="config">
		<echo msg="[config] start Replace config"/>
		<copy file="./config/database.template.php" tofile="./config/database.php" overwrite="true">
			<filterchain>
				 <replacetokens begintoken="env('" endtoken="')">
					<token key="DB_HOST" value="'${DB_HOST}'" />
					<token key="DB_DATABASE" value="'${DB_DATABASE}'" />
					<token key="DB_USERNAME" value="'${DB_USERNAME}'" />
					<token key="DB_PASSWORD" value="'${DB_PASSWORD}'" />
					<token key="DB_PORT" value="${DB_PORT}" />
				 </replacetokens>
			</filterchain>
		</copy>
		<echo msg="[config] end Replace config"/>
	</target>

cmd执行 ```phing config```
