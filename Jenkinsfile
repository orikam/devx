#!/usr/bin/env groovy

node('master') {
	deleteDir()
	checkout scm
	dir('swx_ci') {
		checkout([$class: 'GitSCM', 
				extensions: [[$class: 'CloneOption',  shallow: true]], 
				userRemoteConfigs: [[ url: 'https://github.com/Mellanox/swx_ci']]
				])
	}
	def funcs = load "${env.WORKSPACE}/swx_ci/template/functions.groovy"
	def jjb_pipeFile = funcs.getProjFile("proj_pipeline.groovy")
	evaluate(readFile("${jjb_pipeFile}"))
}
