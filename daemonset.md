#Daemonset
  kind: DaemonSet


#volume mounts

        volumeMounts:
        - name: vol
          mountPath: /mount
      volumes:
      - name: vol
        hostPath:
          path: /configurator

#commands:
command:
          - sh
          - -c
          - 'echo aba997ac-1c89-4d64 > /mount/config && sleep 1d'
