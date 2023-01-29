.PHONY: build

build:
	sam build

deploy-infra:
	sam build && aws-vault exec clemenkok --no-session -- sam deploy

deploy-site:
	aws-vault exec clemenkok --no-session -- aws s3 sync ./resume-site s3://yskclem4cr3