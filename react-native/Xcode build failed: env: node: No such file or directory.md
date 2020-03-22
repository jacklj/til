Xcode cant find node, due to nvm.

Either change node permissions: https://github.com/nvm-sh/nvm/issues/1702#issuecomment-444309875

or change all build phase scripts in the Xcode project that use node, to get node via nvm: https://docs.sentry.io/clients/react-native/manual-setup/
